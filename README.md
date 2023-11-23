### Part 1: Dockerizing a Single Flask Application 

First, I based my docker file and app.py file off the template used in the class demo. Just like class, I modified it to be accessible from any IP address on port 5000. I also made sure to have a requirements.txt file with "flask" in it. Before building the Docker image, I chose a python image from [Docker Hub](https://hub.docker.com/_/python). Then, to build the Docker image based on my Docker file, I ran the "docker build -t bonnie ." command, which builds the image and specifying and tagging the image to be named "bonnie". It is crucial to add a " ." at the end of the command as it represents the context of the build and tells Docker to use the current directory. Then, I ran the command "docker run -d -p 8005:5000 bonnie" to run in detached mode/background and mapping the port 8005 on the host to port 5000 on the container. You can also view the images using "docker images" command. This should then generate a link to view the app.  

### Part 2 Dockerizing with Docker Compose

First, I created two flask apps, each distinct while pulling different images from the Docker Hub. I made sure each followed the same structure with individual app.py, docker file, and requirements.txt file. However, the docker-compose.yaml file has to be located outside of the two flask apps. To build Docker Compose services, I ran the command: "docker-compose build". This would then prompt the two links to be generated to access the two flask applications as shown in class. However, I faced an cloud authentication error because I had used my google shell in my person email and I couldn't authenticate the google cloud without it being  in my school email and without setting everything up from start in my school email google shell. However, if it worked following the class demo, to run the Docker Compose services , run the command: "docker-compose up". To run the Docker Compose services in the background, run the command: "docker-compose up -d". To stop, run the command: "docker-compose down". To view the running containers, run the command: "docker-compose ps".

### Docker Compose vs Docker Alone

#### Docker Alone
-Each container needs to be managed individually (including variables, parameters,ect)
-Can be more complex if you run multiple containers
-Harder to manage distinct apps and less organized
-Can only start one container at a time
-Entirely command line based

#### Docker Compose
-KEY DIFFERENCE: Reads configuration data from a YAML file
-Configure and run multiple containers
-Can define services, paramenters and volumes in a single file to simplfy configuration 
-Can manage the lifecycle of multiple services (building, starting, stopping)
-Can link containers and define dependencies between services
-Highly preferred among users
