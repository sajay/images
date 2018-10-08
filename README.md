# images
Docker images
1. To Build the image : Go to the images directory where the Dockerfie is present and run 'docker build -t test_image .'
2. To run the image : 'docker run -it --rm --name=test_image ubuntu /bin/bash'
3. To see the docker containers : docker ps -a
4. To see the logs : docker logs -f <container id>

To start with, use the below image :

* docker build -t="alessandroadamo/ubuntu-ds-python3" github.com/alessandroadamo/ubuntu-ds-python3

* sudo docker run -it alessandroadamo/ubuntu-ds-python3 /bin/bash

Once done, cleanup the unused containers & images with the below command :

docker system prune -a
