

Run commands on a started container:

    docker container exec -it <cname> sh
    docker container exec -it <cname> python --version
    docker container exec -it <cname> touch test.txt
	
Network Related Commands:
    Docker containers use the bridge network by default
	
	docker network ls
    ifconfig bridge
    docker container run -it -d --name <cname> python:2.8-alpine
    docker network inspect bridge
		-will see the cname in the list of containers
    docker exec <cname> ifconfig
		-run ifconfig on the cname container
		-# To get ipaddress in alpine, add the below in the Dockerfile
		-RUN apk update 
		-RUN apk add iputils
		-#for debian add the below lines
		-#RUN apt-get update
		-#RUN apt-get install -y net-tools iputils-ping
		-Rebuild cname
    	-docker container ls
    	-docker container stop <cname>
    	-docker image  build -t python:2.7-latest .
    	-docker image ls
    	-docker container ls
    	-docker container run -it -d --name cname --rm -p 5000:5000 -e FLASK_APP=app.py -e FLASK_DEBUG=1 -v $PWD:/app python:2.7-latest .
    
	docker exec cname ifconfig
    docker exec c2name ifconfig
    docker exec cname ping 172.17.0.3
		-ping c2name from cname
    docker exec c2name cat /etc/hosts
	
    docker network create --driver bridge firstnetwork
    	-Create your own network
	docker network inspect firstnetwork
    docker container stop cname
    docker container stop cname2
    docker container rm cname2
    docker container run -it -d --name cname2 --net firstnetwork python:2.7-latest
    docker container run -it -d --name cname --net cname --rm -p 5000:5000 -e FLASK_APP=app.py -e FLASK_DEBUG=1 -v $PWD:/app 
    	-Associate the containers with the new network
    docker network inspect firstnetwork
    docker exec container cname ping 172.18.0.2
    docker exec cname2 cat /etc/hosts
    docker exec cname ping cname2
		-Ping cname2 w/o ipaddress


Named Volumes to persist data:

    docker container ls
    docker volume create named-vol-name-db
    docker volume ls
    docker volume inspect named-vol-name-db
    docker container stop cname2
	
    docker container run -it -d -p 6379:6379 --name cname2 --net firstnetwork -v named-vol-name-dv:/data redis:3.2-alpine

    docker volume inspect named-vol-name-db
	
    
	
Clean all images/containers:    
	-docker system prune -a
