# Docker with spring boot

**Docker** is a took designed to make it easier to create, deploy, and run applications by using containers.

**Containers** allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package.

An **image** is a lightweight, stand-alone, executable package that includes everything needed to run a piece of software, including the code, a runtime, libraries, environment variables, and config files.

Docker **networking** to allow multiple containers to interact with each other. With same networking, those containers can communicate together.

So an existing fellow developer will create an image of the environment and share it with the new developer. The new developer wil just have to run the image as a docker container.

### Some use of dockers for Java developer.

* Sharing development workspace, with preconfigured developement environment.
* Continous integration is one of the most popular use cases for Docker. Teams looking build and deploy their applications quickly use Docker, conbined with ecosystem tools like Jenkins, to drive apps from dev, testing staging and into production without having to change any code.
* Running UAT's using Docker.

### Docker compose

Compose is a tool for defining and running multi-container docker application. With Compose, you use a YAML file to configure your application's serviecs. Then, with a single command, you create and start all the services from your configuration.

It will help reducing some steps manualy likes:

* Create custom docker network
* Start containers and link together

Using compose is basically a three-step process:
* Define your app's environment with a Dockerfile so it can be reproduced anywhere
* Define the servies that make up your app in docker-compose.yml so they can be run together in an isolated environment.
* Run docker-conpose up and Compose starts and runs your entire app.

### Some useful commands

* Start docker
 
```systemctl start docker```

* Build image

```docker image buid -t [image_name] .```

* Start docker

```docker container run -d [image_name]```

* Start docker with linking the docker internal port 8080 to external port 8080

```docker container run -p 8080:8080 -d [image_name]```

* Start docker with network

```docker container run --network [network_name] -d [image_name]```

* Start docker with container name

```docker container run --name [container_name] -d [image_name]```

* View inside the docker 

```docker container exec -it [container_id] /bin/sh```

* List containers

```docker container ls```

* View log of container

```docker container logs [container_id]```

* Stop container

```docker container stop [container_id]```

* List images

```docker image ls```

* List networks

```docker network ls```

* Create your own network with type bridge

```docker network create [network_name]```

### Some useful commands on file
##### Docker
* Deploy spring based war application to docker

```
From tomcat:8.0.51-jre8-alpine
RUN rm -rf /usr/local/tomcat/webapps/*
COPY ./target/[war_file].war /usr/local/tomcat/webapps/ROOT.war
CMD ["catalina.sh","run"]
```

* Deploy spring based jar application to docker

```
From openjdk:8
copy ./target/[jar_file].jar [jar_file].jar
CMD ["java","-jar","[jar_file].jar"]
```
* Run docker-compose

```docker-compose up```
