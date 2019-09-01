+++
Categories = ["Development","iOS",]
Description = "Simple guide to build iOS app with buck"
Tags = ["Development","Tutorial","iOS","Swift"]
date = "2017-07-09T10:05:07+07:00"
menu = "main"
title = "Buck build system for iOS Tutorial"

+++

[Buck](https://buckbuild.com/) is a build system created by facebook and it is also used by Uber and Airbnb to increase their productivity by speed up the Build Time.

# Installation
Buck can be installed on mac using homebrew
```
brew tap facebook/fb
brew install buck
```

# Setup Buck for the ios app
 To use Buck for iOS put the .buckconfig and BUCK file in the ios root project, from the gist below (please note "Palmerah" is an Swift iOS project that using Buck, please adjust the folder name and file)

{{< gist bopbi 497ad2eedb3d27461e1b7c0b71673a63 >}}

To adjust xcode properly with buck, go to root folder and type

```
buck project --ide xcode
```

# Build / Run app using Buck
To build the app, go to the xcode project root folder and type
```
buck build :App
```

To build the app and run it on the simulator, go to the xcode project root folder and type
```
buck install --run :App
```

Happy Buck-ing

### Reference:

Android

- [OKBuck, Used Buck with Gradle](https://github.com/uber/okbuck)
- [Lightning Fast Android Build With Gradle by Gradle + Buck. Talks by Uber](https://speakerdeck.com/kageiit/lightning-fast-android-builds-with-gradle-plus-buck)
- [OKBuck slide](https://speakerdeck.com/horie1024/buck-okbuck-sosite-okbazel)
- [Buck Build System](http://zserge.com/blog/buck-build-system.html)


iOS

- [Buck sample from airbnb](https://github.com/airbnb/BuckSample)
- [Fast scaling iOS at Uber](https://atscaleconference.com/videos/blazing-fast-scaling-ios-at-uber/)
- [Buck as an alternative build too from Realm news](https://news.realm.io/news/altconf-uri-baghin-buck-an-alternative-build-tool/)
- [Uber monorepo using Buck](https://eng.uber.com/ios-monorepo/)