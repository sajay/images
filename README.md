# images
Docker images
To Build the image : Go to the images directory where the Dockerfie is present and run 'docker build -t test_image .'
To run the image : 'docker run -it --rm --name=test_image ubuntu /bin/bash'
To see the docker containers : docker ps -a
To see the logs : docker logs -f <container id>
