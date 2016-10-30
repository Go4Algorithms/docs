# Setting up the Go Playground

This guide outlines how to setup the official Go playground (backend) and a modified Go playground (frontend + backend).

## Requirements

* Linux/OSX
* Docker
* Go

## Setting up the official Go Playground

This will setup the backend for the official go playground

```bash

git clone https://github.com/Go4Algorithms/playground.git
cd playground
docker build -t sandbox sandbox/ # Compile the docker image
docker run -d -p 8080:8080 sandbox # Run the image as a container

```

*NOTE: For the official playground, setting up the frontend is still under investigation*

## Setting up unofficial Go playground w/ frontend

This will setup a custom playground with a frontend. It should be noted that there are some changes in how data is handled here so curl requests that work on the official version of the playground will not work with this fork. This version comes with a makefile for the various components so compiling should be fairly straightforward.

```bash

git clone https://github.com/Go4Algorithms/go-playground.git

# Setup the backend sandbox
cd sandbox
make docker
make run

# Setup the webapp
cd webapp
go build
./webapp -allow-share -s "http://localhost:8080/compile?output=json"
# Webapp requires the backend sandbox to be running on port 8080

```
More information on setting up the custom sandbox can be found at: https://github.com/Go4Algorithms/go-playground  
