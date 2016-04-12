# Docker-out-of-Docker
(DooD) How to run Docker commands within Jenkins within a Docker container 

# Plugins
The dockerfile allows you to setup Jenkins with pre-existing plugins. You can edit the file to include whichever plugins you want or need, but for the sake of running Docker commands with sudo, you must include "scm-api" as a plugin.


# Steps
To build the image using the dockerfile, use the command:
docker build -t jenkins-with-docker .

To run the container, use the command:
docker run -d -v /var/run/docker.sock:/var/run/docker.sock \
                -v $(which docker):/usr/bin/docker -p 8080:8080 jenkins-with-docker

You should now have a jenkins container running on port 8080.
You can now run docker commands with "sudo docker"