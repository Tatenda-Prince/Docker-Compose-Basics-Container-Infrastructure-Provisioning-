# Docker-Compose-Basics-Container-Infrastructure-Provisioning-
"Construct Container Compose"

![image alt](https://github.com/Tatenda-Prince/Docker-Compose-Basics-Container-Infrastructure-Provisioning-/blob/6bb0048362a93327fc6ec6c87619ec1808b94b7f/Images/Screenshot%202024-12-28%20112152.png)

# Intro 
This is a continuation of my previous project where I took you through how we can use Docker’s fundamental commands and concepts by creating a Python/Boto3 development environment that involved building a custom image, running containers and creating bind mounts.

Today, we are going to take it a step further to use a Docker Compose file to build/provision an infrastructure of running container according to the configurations written in the file.


# Docker Compose Information

# Docker Compose

Docker-compose reads configuration data from a Docker Compose YAML file usually named “docker-compose.yml” to provision container application services.

# Docker compose up

The “docker compose up” command starts and restarts all the services defined in the docker-compose.yml file.

# Docker compose down

The “docker compose down” stops and removes all containers and networks created by the docker-compose.yml file.

# Docker inspect <container_name>

The “docker inspect <container_name>” command lists extensive and complete information of the container provided.

# Prerequisites

Basic knowledge and understanding of containerization and Docker

Basic Linux command line knowledge

Basic knowledge and use of an Interactive Development Environment (IDE).

# Step 0: Set up environment

first, head on to open our terminal, Using Ubuntu WSL2 we are going to install Docker and Docker compose, then run the following commands-

sudo apt update

sudo apt install docker.io docker-compose -y 

# Step 1: Configuring the docker-compose.yml file

On our termianl we are going to make a new directory called Chels and cd into to create a file docker-compose.yaml

![image alt](https://github.com/Tatenda-Prince/Docker-Compose-Basics-Container-Infrastructure-Provisioning-/blob/f70ced21afefd86f95b6adfcf28e9797a65ea6bc/Images/Screenshot%202024-12-28%20123327.png)


Let’s dive into what’s happening in this file —

As we know, this is a Docker Compose file that defines a set of services and their configurations.

The file begins with specifying the version of the Docker Compose syntax that the file is using, which is version 3.

1.Service: Defines the services (containers) to be created.

2.Wesite: The name of the service, which will host the website.

3.Image: Specifies the Docker image to use for the service. Here, it uses the official Nginx image, a lightweight and efficient web server.

4.Ports: Maps ports from the host machine to the container.

  8081:80 : Maps port 8081 on your machine to port 80 inside the container (the default HTTP port used by Nginx). You can access the Nginx server at http://localhost:8081.

5.Restart: Ensures the container automatically restarts under certain conditions.

6.Always: The container will restart anytime it stops, whether due to failure or manual intervention.


Now lets run our docker-compose.yaml to see what happens by running this command-

docker compose up -d 


![image alt]()


Now lets check wheather our website works by going to our local browser and typing - localhost:8081

![image alt]()


We did get a welcome message informing us that our website is working. 


What if we want to delete the container, we can simply run this command - 

sudo docker compose down

as you can see from below our container was deleted successfully


![image alt]() 


we can also simply bring it to running by entering sudo dockerr compose up -d 








  













