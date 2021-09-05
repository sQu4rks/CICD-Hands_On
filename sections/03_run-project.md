# Hands-On: Run the project locally

**In this Section we will:**
* Run a Redis Container
* Clone the github repository
* Build the docker image
* Run the docker images (app + redis) locally

## Cloning the GitHub repository

Change to a directory of your preference and use `git clone https://github.com/sQu4rks/CICD-Hands_On-Demo.git`  to clone the repository with the app and all required files for this session to a new folder.

Create a virtual environment to work inside during our session?

P.S.: To clone the repository with this sessions text you can use `git clone https://github.com/sQu4rks/CICD-Hands_On.git`

## Running the Redis container

Verify Docker is running:
Try `docker -v` or `docker ps` to check if docker is running.

To verify the installation, run the `hello-world` container from Docker using `docker run hello-world`
Verify that the docker installation is working correctly. You should see the following output:

```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

...
```

To get the redis container downloaded and running, do the same thing using `docker run redis` which will pull the latest version of redis from DockerHub and start the container.

## Build and run the Docker container

To run both images locally we can use docker Compose, which is a tool for defining and running multi-container Docker applications. Refer to the `docker-compose.yaml` file in the repository. 

To build the images with Compose, you can use `docker-compose build`. To start them use `docker-compose up` and to stop the containers `docker-compose down`. In our case we have already build the image with Docker and pushed it to DockerHub, where the images can be pulled from anywhere.



<div align="right">
   
   [Prev](02_intro-to-code.md) - [Next](04_intro-to-deployments.md)
</div>
