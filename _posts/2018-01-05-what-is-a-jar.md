---
layout: post
title: "What in the world is a JAR?"
date:  2018-01-05
comments: true
categories: jekyll update
---

![Little donuts in a glass jar]({{ GeorgeSmith-Sweeper.github.io }}/assets/donutsInJar.jpg){:class="img-responsive"}

Yes this is in fact a jar (a delicious one at that), but it's not the type of jar we're going to be talking about.
The __JAR__'s we're looking for are in the programming language Java. __JAR__ stands for __J__-ava __AR__-chive. and let you bundle up all of your application classes into a neat and compact file.

### When do you need a JAR?

JAR files are based on the `pkzip` format, and can be used for compression, archiving, and unpacking. Most developers use JAR's during the final stages of a project to consolidate their project files into a single executable that the client can run.

### How is a JAR created?

In order for a JAR file to work properly you must create a file called "manifest.txt". This manifest file tells the JVM which compressed and packaged file inside the JAR is your "entry point" and contains the `main()` method.

```java
// inside manifest.txt
Main-Class: App  // <---- this is the name of the class where main() lives

```

Building a JAR works with the command line `jar` tool.

You can run `jar -cvmf manifest.txt myJar.jar App.class` from the command line, and the tool will grab your manifest file, add it to the JAR named "myJar.jar" along with the classes that are necessary to run your application.

```
 _________          _________          ____________
|         |        |         |        |            |
| classes | -----> |  myJar  | <----- |  manifest  |
|_________|        |_________|        |____________|

```

### How can you run a JAR?

Once a JAR has been created you'll probably want to tell your client / friend / anyone how to execute it, and get your application running.

If the person running the application happens to be in the classes directory, they can simply run `java -jar myJar.jar` otherwise you'll have to give them the full path to the jars location (within the classes directory). This command tells the JVM that you're giving it a "jar" file, and that it should look inside the manifest file for the `main()` method.

The JVM is smart enough to understand how to read JAR's and will take care of the execution process.

## Summary

__JAR__ files are one of Java's great tools to streamline the deployment process. Most local apps (non-web) are deployed as executable JAR's so that developers don't have to manually handoff every class required to run their app.

{% include disqus.html %}
