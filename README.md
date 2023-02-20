# go-helloworld-docker

### Step 1. Get the Dockerfile ready
```
# use the golang:alpine base image
FROM golang:alpine

# set the working directory to /go/src/app
WORKDIR /go/src/app

# copy all the files from the current directory to the container working directory
ADD . .

# import dependencies using `go mod init` and build the application using `go build -o helloworld` command
RUN  go mod init && go build -o helloworld

# expose the port 6111
EXPOSE 6111

# start the container
CMD ["./helloworld"]
```

### Step 2. Package the application
Steps to package the application using Docker commands:

``` 
# build the image
docker build -t go-helloworld .

# run the image
docker run -d -p 6111:6111 go-helloworld

# tag the image
# change the Dockerhub username, as applicable to you, for e.g., tomato/go-helloworld:v1.0.0
docker tag go-helloworld tomato/go-helloworld:v1.0.0

# login into DockerHub
docker login

# push the image
docker push tomato/go-helloworld:v1.0.0
```
