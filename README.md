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


![image alt](https://github.com/Tatenda-Prince/Docker-Compose-Basics-Container-Infrastructure-Provisioning-/blob/c9457de4c90c0fd3819095ee13bb4a855e23af71/Images/Screenshot%202024-12-28%20131131.png)


Now lets check wheather our website works by going to our local browser and typing - localhost:8081


![image alt](https://github.com/Tatenda-Prince/Docker-Compose-Basics-Container-Infrastructure-Provisioning-/blob/c976437d23cf98574f9d71c940c4fe92fdd8ae81/Images/Screenshot%202024-12-28%20130240.png)


We did get a welcome message informing us that our website is working. 


What if we want to delete the container, we can simply run this command - 

sudo docker compose down

as you can see from below our container was deleted successfully


![image alt](https://github.com/Tatenda-Prince/Docker-Compose-Basics-Container-Infrastructure-Provisioning-/blob/775b8d6d8a7c9af7611ee43a0c959bb4657072fe/Images/Screenshot%202024-12-28%20131038.png) 


we can also simply bring it up to running by entering : sudo dockerr compose up -d 

Now lets move on to step 2 where we will create multiple containers using the docker-compose.yaml


# Provision multiple containers and add Networks

So basically we are going to add another container to our previous existing yaml file and name it website2 and add a network .
We are are going to: nano docker-compose. yaml 


![image alt](https://github.com/Tatenda-Prince/Docker-Compose-Basics-Container-Infrastructure-Provisioning-/blob/28d71e008d87afda7958caf75df48cbb44d3ad7c/Images/Screenshot%202024-12-28%20133544.png)


Let’s dive into what’s happening in this file —

1.Networks: Configures the service to connect to a user-defined network (chels) with a specified IP address.

2.ipam: Defines custom network settings for the (Chels) network.

3. Driver: Default
    Uses Docker's default networking driver (bridge driver).

4. Config: Configures the network's subnet:
    subnet: "192.168.92.0/24"
   
Specifies the subnet for the chels network, allowing IP addresses from 192.168.92.1 to 192.168.92.254.


So lets save the file and test it out to check if it is working-
We are going to run - sudo docker compose up -d again 

As you can see from below our new container websit2 was created successfully.

![image alt](https://github.com/Tatenda-Prince/Docker-Compose-Basics-Container-Infrastructure-Provisioning-/blob/0aec240fac18dba82bf0a850903c7c4a5a3e70bb/Images/Screenshot%202024-12-28%20135705.png)



Now lets go on to verify our networking by running -
sudo docker networking ls 

As you can see from below we now have two docker composed networks the Default that was created by docker and the other one that we specified.

![image alt](https://github.com/Tatenda-Prince/Docker-Compose-Basics-Container-Infrastructure-Provisioning-/blob/54c78c70f5550d45e0b2952e4191316c4104818b/Images/Screenshot%202024-12-28%20140022.png)


Now if we run Docker inspect we should be able to see our container with the IP Address we configured ealier.
run- sudo docker inspect 


![image alt](https://github.com/Tatenda-Prince/Docker-Compose-Basics-Container-Infrastructure-Provisioning-/blob/e185f7bea420e34864f0e8b5211f775c24c8cc3e/Images/Screenshot%202024-12-28%20141001.png)


# Step 3: Deploying a WordPress Website





















  













