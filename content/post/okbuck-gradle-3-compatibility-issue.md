+++
Categories = ["Development","Android","Build"]
Description = "Okbuck compatibility issue with Gradle 3"
Tags = ["Development","android","okbuck","gradle"]
date = "2017-08-04T09:14:10+07:00"
menu = "main"
title = "Okbuck gradle 3 compatibility issue"

+++

When i am using [okbuck](https://github.com/uber/okbuck) to speed up my build time, the build is always failed and on the console it show:

```

buck-out/gen/app/res_debug#resources-symlink-tree/res/values/styles.xml:4: error: Error retrieving parent for item: No resource found that matches the given name 'Theme.AppCompat.Light.DarkActionBar'.

```

first i think it have some issue with the Android AppCompat, and when i try to perform an installation it show

```

error: unresolved reference: support
import android.support.v7.app.AppCompatActivity
               ^

```

well that mean i the appcompat dependency is not exist on the okbuck

this is my dependencies on my build.gradle:

```

dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    androidTestImplementation ('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    implementation 'com.android.support:appcompat-v7:26.0.0'
    testImplementation 'junit:junit:4.12'
    implementation 'com.android.support.constraint:constraint-layout:1.0.2'
}

```

Well i noticed the dependencies is now using **implementation** rather than **compile**, the **implementation** is introduced on *Gradle 3*, reference [https://stackoverflow.com/questions/44493378/whats-the-difference-between-implementation-and-compile-in-gradle](https://stackoverflow.com/questions/44493378/whats-the-difference-between-implementation-and-compile-in-gradle)

i try to change the **implementation** to the **compile** so my build.gradle file will be like:

```

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    androidTestCompile ('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    compile 'com.android.support:appcompat-v7:26.0.0'
    testCompile 'junit:junit:4.12'
    compile 'com.android.support.constraint:constraint-layout:1.0.2'
}

```

now on the console it show that the okbuck is importing the dependencies

well it seem the okbuck hasn't yet support the implementation, androidTestImplementation, and testImplementation