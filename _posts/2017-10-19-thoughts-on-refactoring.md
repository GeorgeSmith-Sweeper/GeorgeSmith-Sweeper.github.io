---
layout: post
title: "Thoughts on Refactoring"
date:  2017-10-19
comments: true
categories: jekyll update
---

I'm not the greatest at refactoring, often struggle when it comes to identifying which pieces of my existing code base can be changed, and have trouble coming up with a strategy for cleaning my code.

Normally a strong signal to refactor is when I begin to notice duplication in my application, or  nested conditional logic in a method. This approach has worked well for me as long as I make sure to refactor immediately.

In order to help me identify refactor points more quickly, my mentors have suggested that I read 'Refactoring - Ruby Edition' for the past couple of days. I'm not a refactoring master yet, but i'm starting to understand that there are other, more subtle signals that should trigger a refactor.

### Code Smells

__Long Methods__

>The longer a procedure is, the more difficult it is to understand.

Do you understand whats happening in this method?

```python
    def add_to_board(self, all_ships, place, ship_orientation):
        all_ships_copy = all_ships.copy()
        ship = 0
        row_int = place.create_random_num()
        col_int = place.create_random_num()

        while len(all_ships_copy) > 0:
            if ship_orientation == 'row':

                while place.can_ship_fit_in_row(self.state, all_ships_copy[ship]['size'], row_int, col_int) == False:
                    row_int = place.create_random_num()
                    col_int = place.create_random_num()

                for ele in range(all_ships_copy[ship]['size']):
                    self.state[row_int][ele - (len(self.state) - col_int)] = all_ships_copy[ship]['symbol']
            else:
                while place.can_ship_fit_in_column(self.state, all_ships_copy[ship]['size'], row_int, col_int) == False:
                    row_int = place.create_random_num()
                    col_int = place.create_random_num()

                for ele in range(all_ships_copy[ship]['size']):
                    self.state[ele - (len(self.state) - row_int)][col_int] = all_ships_copy[ship]['symbol']

            all_ships_copy.pop(0)
            ship_orientation = 'column' if ship_orientation == 'row' else 'row'
```

No? Well neither do I, and I wrote it two days ago... This is a perfect example of a method that is too long (with lots of duplication). I plan to fix it by extracting the duplicated logic into smaller methods, and then calling them within the original `add_to_board` method.

__Speculative Generality__

>Speculative Generality can be spotted when the only users of a method, class, or branch, are test cases.

This doesn't happen that often in my code, but typically appears when I've attempted to plan ahead, and anticipate what might objects or classes might be needed for future feature requests.

These classes should be removed immediately.

__Painful Feature Addition__

>When you find you have to add a feature to a program, and the programs code is not structured in a convenient way to add the feature, first refactor the program to make it easy to add the feature, then add the feature.

Essentially if you dread having to make changes to your program, it has become very rigid, and can be simplified.

I still have a number of features that need to be implemented in my Battleship game, and I can already foresee one particular request that is going to cause trouble. Time to refactor!

### Solutions

'Refactoring - Ruby Edition' doesn't offer any silver bullets to fixing code, and I honestly haven't gotten far enough through the book to know if there were any. I plan on taking the rest of the day to refactor some of my Battleship game code, while keeping the book open next to me as a reference.

I will update this post, and do a follow up once the solutions become more clear to me.
