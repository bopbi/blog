+++
Categories = ["Development", "GoLang"]
Description = "Fix on Docker installation"
Tags = ["Development", "golang"]
date = "2016-01-08T00:03:58+07:00"
title = "Docker eval issue"

+++

After i followed [the Docker installation step](https://docs.docker.com/mac/step_one/) on my mac, start the Docker Quickstart Terminal app, and try to run the hello-world app, it will show an error that say it cannot connect to the Docker daemon as shown below:

    Cannot connect to the Docker daemon. Is the docker daemon running on this host?
    
Reinstalling Docker using the installer on the docker website didn't fix this issue

After i googled around this issue, it seems this issue is caused by the docker-machine environment variable is not properly set with the running vm.

The solution is run the eval for the environment, type line below on the terminal (default is the name of the running vm) every time after running the Docker Quickstart app

    eval $(docker-machine env default)
   
now it works flawlessly