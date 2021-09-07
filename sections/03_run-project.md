# Hands-On: Run the project locally

Now after you got to know our little app, we will prepare everything to run it locally with Docker.

First, change to a directory of your preference and use `git clone https://github.com/sQu4rks/CICD-Hands_On-Demo.git`  to clone the repository with the app and all required files for this session to a new folder.

P.S.: To clone the repository with this sessions text you can use `git clone https://github.com/sQu4rks/CICD-Hands_On.git`

Now that we have all files, we can start checking on our environment. Please verify Docker is functioning proberly, you can try `docker -v` or `docker ps` to check if docker is running.

To verify the installation, run the `hello-world` container from Docker using `docker run hello-world`
If everything works as intended, you should see the following output:

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

Now that we have verified the Docker intallation, let's get our app running.

To run both images locally we can either build and run them locally together and configure them manually, or we use `docker-compose` - which is a tool for defining and running multi-container Docker applications. Check out the `docker-compose.yaml` file in the repository to see what is configured for us already.

To build the images with Compose, you can use `docker-compose build`. To start them use `docker-compose up` and to stop the containers `docker-compose down`. In our case we have already build the image with Docker and pushed it to DockerHub, where the images can be pulled from anywhere at a later point in time. With docker-compose, we will see both images being pulled and the corresponding containers being created. We can now start to interact with our local deployment of our guestbook app.

<div align="right">
   
   [Prev](02_intro-to-code.md) - [Next](04_intro-to-deployments.md)
</div>
