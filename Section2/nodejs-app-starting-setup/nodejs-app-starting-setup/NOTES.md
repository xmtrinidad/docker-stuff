# Managing Images & Containers

## Images

*  Can be tagged (named)
    * -t, dockter tag ...

* Can be run
    * docker run -p 8000:80 imageID
    * docker run -p 8000:80 -d imageID

* Can be listed
    * docker images

* Can be analyzed
    * docker image inspect


* Can be removed
    * docker rmi, docker prune


## Containers

* Can be named
    * --name

* Can be configured in detail
    * see --help

* Can be listed
    * docker ps
    * docker ps -a