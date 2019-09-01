---
title: "Android app lib Dependencies Tree"
Description: "My Story on how to see dependencies of the library that we are using in android development"
date: 2018-05-10T22:11:15+07:00
draft: false
Tags: ["Development","android"]
---

On my company app, i noticed that the app is using two different Rxjava version (1 and 2) and of course i want to use the latest.

So i am searching any code that are using the old version, but there are no import that using the old version, so it must be related with the library, and after googling it i found that i can be easily found using the gradle command:

```
./gradlew app:dependencies
```

after that just perform search on the terminal based on the lib package name.

* please note it will generate a very-very long line in the console make sure you set the scrollback line to a large number, for me i get the library name after set it to 5000 lines

**screenshot:**

![capp_lib_tree](/img/app_lib.png)