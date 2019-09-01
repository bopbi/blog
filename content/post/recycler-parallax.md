+++
Categories = ["Development", "Android", "UI", "Library"]
Description = "Parallax sample code for Recyclerview on Android"
Tags = ["Development", "Android"]
date = "2015-11-15T21:54:01+07:00"
title = "Recycler Parallax"

+++

Recycler Parallax is an android code example that show parallax effect on a recycler view for each item when it is scrolled, this library is inspired by soundcloud android app.

Steps that i use to achieve the parallax event:

* Set the image matrix to center vertically, using RecyclerView Adapter onBindViewHolder method.
* Reset the image matrix on RecyclerView Adapter on method onViewRecycled.
* Handle the scroll movement by using the RecyclerView onScrollListener.
* During scroll, manipulate the image matrix of the visible image on the RecyclerView.

please take a look at the source on [github](https://github.com/bopbi/RecyclerParallax/) and the video below

{{< youtube 8dxKiSZr24s >}}