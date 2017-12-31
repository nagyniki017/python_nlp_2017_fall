# Start an existing Docker container

Your container from previous week(s) is available on the same machine you used last time.
Start Docker and Powershell.

Find out the name and id of your container:

    docker ps -a

This command lists every container including the stopped ones (all of them are stopped at this point).

The third column lists the image's name, find `juditacs/python_nlp`.

The first column is the id of the containers and the last column is their name.

Start your old container:

    docker start <container id or name>

(tip: if you use the id, it is enough to specify the first few letters, as long as it's not ambiguous)

Check your running container:

    docker ps

You should see one running container.

Start a shell in the container:

    docker exec -it <container id or name> bash
 
Have fun.

# Docker instructions

* start Windows WITH Hypervisor
* start Docker (icon on Desktop)
  * you may have to start it twice
  * Docker takes a while to start, you can check its status on the taskbar
  * if it fails to start, you have to reduce the memory allocated for Docker to 1.5GB or 1GB
  * Right click on the Docker logo on the taskbar -> `Settings / Advanced`, set memory
* Make sure that drive D is shared under `Shared Drives`
* start PowerShell
* pull the image from Docker hub


    `docker pull juditacs/python_nlp`


Start the image in a new container and execute bash in one command


    docker run -p 8888:8888 -it juditacs/python_nlp:latest bash


This command will forward the container's 8888 port to the host system's 8888 port. We will use this port to connect to Jupyter.


## Directories

The course's repository is already cloned into `/nlp/python_nlp_2017_fall`. Don't forget to pull the latest version:

    cd /nlp/python_nlp_2017_fall && git pull

The Hungarian HFST model is available at `/nlp/hfst/hu.hfstol`.

## Running Jupyter inside the container

    jupyter notebook --port=8888 --ip=0.0.0.0 --no-browser --allow-root

This will print a url that contains jupyter's login token, copy and paste it into a browser on the host machine.


## Docker quick intro

List running containers:

    docker ps

List existings containers:

    docker ps -a

Start a container

    docker start <container name or id>

Execute a command in a running container (the command is always going to be `bash` for now):

    docker exec -it <container name or id> <command>

Start a container and execute a command in it:

    docker run -it <container name or id> <command>

Delete container:

    docker rm <container name or id>

List images:

    docker images

Delete image:

    docker rmi <image name or id>
