+++
Categories = ["Development", "iOS"]
Description = "Note on viewDidDissapear"
Tags = ["Development", "iOS"]
date = "2015-11-13T22:18:31+07:00"
title = "iOS set root view controller wont call viewDidDissapear"

+++
I noted some behaviour when performing set a root view controller on iOS.

Strangely it wont call the viewDidDissapear method on the viewController that are set the root view controller. 

Always please remember to manually unregister all notification of the viewController before performing a set root view controller, or you gonna have to handle multiple notification
