+++
Categories = ["Development","Android"]
Description = "Workaround Idea for Rest Client App on Android O"
Tags = ["Development","android"]
date = "2017-05-17T15:01:53+07:00"
menu = "main"
title = "Android O background services effect on REST Client App"

+++

When creating an Andrioid REST Client app i usually have a Android Service that consume the REST API and Store it on a Content Provider, this technique is coming from an Presentation on 2010 Google IO (see the video below)

{{< youtube xHXn3Kg2IQE >}}

slides for the presentation [https://dl.google.com/googleio/2010/android-developing-RESTful-android-apps.pdf](https://dl.google.com/googleio/2010/android-developing-RESTful-android-apps.pdf)

On that presentation it say to there are 3 basic pattern for a REST client

1. Use Service API
+ Use Content Provider API
+ Use Content Provider API & Sync Adapter


Since on Android O if we call a Service via startService() it will throw a IllegalArgumentException which mean we cannot use the Service by use startService.

Because of Service limitation the Android Team suggest to switch using JobService that introduced on android M (for backward compatibility we can use [FirebaseJobDispatcher](https://github.com/firebase/firebase-jobdispatcher-android) or [Evernote JobService](https://github.com/evernote/android-job)) the JobService basically a service that is run based on certain condition (Network Type, Power Type, Duration, etc) and it cannot run directly it must make some calculation and scheduled before running, it will have some delay and the delay between requesting for running cannot be determined (it depend on Android/Google Play)

Based on the basic patterns for REST client above and the Service limitation it seems the only option to perform REST API calling from background and stored it safely is by using **the Content Provider API & Sync Adapter**

how the Content Provider API & Sync Adapter work (based on my interpresentation of the slide):

1. Activity / Fragment call an REST API via Content Provider asynchronously (use Loader/AsyncTask/Handler/etc)
+ Content Provider is Calling a Sync Adapter to perform REST API Call
+ REST response is stored on the Content Provider
+ Content Provider notify an app using ContentObserver/Loader


a good tutorial for creating a SyncAdapter is on [https://developer.android.com/training/sync-adapters/index.html](https://developer.android.com/training/sync-adapters/index.html) and [http://blog.udinic.com/2013/07/24/write-your-own-android-sync-adapter/](http://blog.udinic.com/2013/07/24/write-your-own-android-sync-adapter/)
