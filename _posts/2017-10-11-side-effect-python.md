---
layout: post
title: "Understanding 'side_effect' in Python "
date: 2017-10-11
categories: jekyll update
---
Today while testing my Battleship game, I hit a wall with testing my game loop. More specifically, I had created a while loop that prompted users to pick a spot on the game board, but had no way to mock out potential responses from the user.

Here's the code:

```python
    def spot_exists(self, ui):
        user_shot_choice = ui.get_input('>>')

        while user_shot_choice not in self.all_spots:
            ui.display('Spot does not exist, Try again')
            user_shot_choice = ui.get_input('>>')
        return user_shot_choice
```

The issue with testing this loop is that once `spot_exists` is called, I have no way to supply my `ui.get_input` (just a wrapper on Pythons built in input()) with a value. To make matters worse, there is a second `ui.get_input` waiting to be called inside of the while loop.

### Enter side_effect

I used a feature from Pythons `unittest` suite called `side_effect` to tackle the input issue. Let's take a look at how the documentation describes this feature.

>This can either be a function to be called when the mock is called, an iterable or an exception (class or instance) to be raised.

>If you pass in a function it will be called with same arguments as the mock and unless the function returns the DEFAULT singleton the call to the mock will then return whatever the function returns. If the function returns DEFAULT then the mock will return its normal value (from the return_value).

>If you pass in an iterable, it is used to retrieve an iterator which must yield a value on every call. This value can either be an exception instance to be raised, or a value to be returned from the call to the mock (DEFAULT handling is identical to the function case).

The last part of definition is the most relevant for me, and allows me mock `ui.get_input`, control what values it returns, and in what order!

Here's what I came up with:

```python
@patch('core.ui.TerminalUi.get_input', side_effect = ['A35', 'A1'])
def test_spot_exists_prompts_the_user_if_spot_is_invalid(self, mocks):
       validate = Validate()
       ui = TerminalUi()
       invalid_msg = 'Spot does not exist, Try again'
       ui.display = MagicMock()

       validate.spot_exists(ui)

       ui.display.assert_called_with(invalid_msg)
```

The first line is the where the magic happens. `ui.get_input` will be called twice, and it's return value will be 'A35', and 'A1' in that order.

Passing in 'A35' for my first value allows me to move into the while loop, and test that my `invalid_msg` is displayed. Passing in 'A1' prevents the while loop from running forever, and ends the test.

Super useful!
