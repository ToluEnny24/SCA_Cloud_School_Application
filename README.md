# SCA_Cloud_School_Application
This repository contains my solution to the task 2 of using docker and a simple webpage using HTML


1.) It is worthy to note that Docker Images start from a base image. This base image includes all the platform dependencies required by your application, for example, having the JVM for Java or CLR installed.

This base image is defined as an instruction in the Dockerfile. Docker Images are built based on the contents of a Dockerfile. The Dockerfile is a list of instructions describing how to deploy your application.

In this task, I used a base image which is the Alpine version of Nginx. This provided the configured web server on the Linux Alpine distribution.

I declared this in the dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html

2 ) The Dockerfile is used by the Docker CLI build command. The build command executes each instruction within the Dockerfile and in this assessment I built a base environment of nginx to help launch the webpage created using html.
The build command takes in some different parameters. 
The format is docker build -t <build-directory>. 
The -t parameter allows me to specify a friendly name for the image and a tag, commonly used as a version number. This allowed me to track the built images and be confident about which version is being started.
. here specified i wanted my docker build action to be inside the current directory I am in.

 docker build -t cloudschool_server:v1 .


The command below is ran inside the terminal. For this task I used
docker build -t cloudschool_server:v1 .

This built an image tagged cloudschool_server with a tag of v1

By running the command docker images, I was able to view a list of all the images on the host.

The built image had the name cloudschool_server:v1.

3) Run the image on the server.
For example, to open and bind to a network port on the host you need to provide the parameter -p <host-port>:<container-port>.

I then launched my newly built image providing the friendly name and tag since it is a web server, by binding port 80 to our host using the -p parameter.

docker run -p {external-port}:{internal-port} {container-name}
docker run -d -p 80:80 cloudschool_server:v1

After this was started, I was able to access the output via localhost:80
 

![cloudschool](https://user-images.githubusercontent.com/70230223/161591873-07be3bb5-6378-4a39-a5ff-f885b2f4249e.PNG)
![Output](https://user-images.githubusercontent.com/70230223/161592010-a9dc1d9d-edaa-4490-89d0-5c6d4f25835f.PNG)
![dockerrun](https://user-images.githubusercontent.com/70230223/161592020-4e7a59bf-5bdf-48f6-af1d-70ec2c2d43bc.PNG)
