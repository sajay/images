# images
Docker images
1. To Build the image : Go to the images directory where the Dockerfie is present and run 'docker build -t test_image .'
2. To run the image : 'docker run -it --rm --name=test_image ubuntu /bin/bash'
3. To see the docker containers : docker ps -a
4. To see the logs : docker logs -f <container id>
