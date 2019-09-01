+++
Categories = ["Development","Android"]
Description = "Story about RecyclerView that wont apply the layout_gravity_ "
Tags = ["Development","android"]
date = "2017-06-24T11:39:03+07:00"
title = "RecyclerView and layout_weight"

+++

During developing an Android app i try to implement a RecyclerView that use a LinearLayout, and each row of consist of a 2 TextView and i use the layout_weight property to distribute the position of each TextView.

During testing somehow it couldn't work as is intended, it wouldn't obey the layout_weight and match_parent are not working, after googling and search on stackoverflow i found that we must and manually the layout params during ViewHolder creation as shown below (code are in kotlin):

```

override fun onCreateViewHolder(parent: ViewGroup?, p1: Int): ScheduleViewHolder {
    val view = LayoutInflater.from(parent?.context).inflate(R.layout.row_custom, null, false)
    val lp = RecyclerView.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.WRAP_CONTENT)
    view.layoutParams = lp
    return CustomViewHolder(view)
}

```