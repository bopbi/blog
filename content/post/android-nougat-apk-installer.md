+++
Categories = ["Development","android"]
Description = "Behaviour of the APK Installer on Android Nougat"
Tags = ["Development","android"]
date = "2017-05-15T19:31:12+07:00"
title = "Android Nougat APK Installer"

+++

Android Nougat are now prohibited the usage the file scheme (file://) on sharing cross app (for intent), and now switch to use the [FileProvider](https://developer.android.com/reference/android/support/v4/content/FileProvider.html) so now on Nougat we must use the content scheme (content://) that also enable an app to share anything on its internalDir to another app, as long as add Intent flags [FLAG_GRANT_READ_URI_PERMISSION](https://developer.android.com/reference/android/content/Intent.html#FLAG_GRANT_READ_URI_PERMISSION)

That also mean the apk installer app of the android also use the content scheme, and that allowed an app to store an APK inside the internalDir and share it to the installer app via an intent. This kind of sharing is cannot be done on android below nougat since the installer app below nougat is still using the file scheme and accessing another app internalDir through file scheme is prohibited for security concern.