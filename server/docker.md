## Docker

If you have VirtualBox running, shut it down before running the installer.

Then install the `docker-tools`.

After installing the `docker-tools` packages, just run the `docker terminal` to start up the default machine.

Then, to see if things are set up run: `docker run hello-world`. You should get an output saying `Hello from docker`

Below are some snippets:

Start the interactive shell using the `ubuntu` image:

`docker run -t -i ubuntu:14.04 /bin/bash`

Start a basic python application using the image. The application then can be seen at: `ipAddress:8998`

`docker run -d -p 8998:5000 training/webapp python app.py`

Get a list of processes runing in docker:

`docker ps`

Stop a process:

`docker stop name_of_process`

Removing an image:

`docker stop name_of_image`
`docker rm name_of_image`

## [Docker Images](https://docs.docker.com/userguide/dockerimages/)

## [Mongodb with Docker for Production](https://medium.com/@arunoda/production-quality-mongodb-setup-with-docker-65136a4a9d8#.acv6itbo2)
