# docker_cheatsheet

1. To install and run docker image
	docker run postgres:13.5

2. To check docker image running
	docker ps

3. To download image 
	docker pull redis(image name)

4. To run docker image run in background
	docker run -d redis

5. To pass default argument
	sudo docker run -e POSTGRES_PASSWORD=kaihiwatari postgres:15.3

6. To restart the docker process
	docker stop container_id
	docker start container_id

7. To check all containers running or not running 	
	sudo docker ps -a

8. To change port (out port and container port)
	docker run -p6000:6379 redis

9. To see all docker images
	docker images

10. To check logs
	docker logs container_id

11. To change name of docker process
	sudo docker run -d -p6000:6379 --name redis-older redis:4.0

12. To debug and see its configuration
	 sudo docker exec -it container_id /bin/bash 

13. Build an Image from a Dockerfile
	docker build -t image_name

14. Build an Image from a Dockerfile without the cache
	docker build -t image_name . -no-cache

15. List local images
	docker images

16. Delete an image
	docker rmi image_name

17. Remove all unused images
	docker image prune

18. Remove a stopped container:
	docker rm container_name

19. Open a shell inside a running container:
	docker exec -it container_name sh

20. Fetch and follow the logs of a container:
	docker logs -f container_name

21. To inspect a running container
	docker inspect container_name (or container id)

22. List all docker containers (running and stopped):
	docker ps --all

23. View resource usage stats
	docker container stats

34. List all docker container
	docker container ls

35. To check docker network list
	docker network ls

36. To create a new network
	docker network create mongodb

Docker compose example

Basic example

# docker-compose.yml
version: '2'

services:
  web:
    build:
    # build from Dockerfile
      context: ./Path
      dockerfile: Dockerfile
    ports:
     - "5000:5000"
    volumes:
     - .:/code
  redis:
    image: redis

commands

docker-compose start
docker-compose stop
docker-compose pause
docker-compose unpause
docker-compose ps
docker-compose up
docker-compose down


Docker volume

1. To list all volume in docker
	sudo docker volume ls 

2. Create a new volume
	sudo docker volume create sample_volume	

3. Inspect volume
	sudo docker volume inspect sample_volume

4. Mounting docker volume
	sudo docker run -it -v sample_volume:/shared-volume --name my-container-01 ubuntu	

5. Create a file inside docker volume
	ls
	cd /shared-volume
	echo "sample_volume" > sample_volume.txt
	ls
	exit

6. Create another container and mount the volume
	sudo docker run -it -v sample_volume:/shared-volume --name my-container-02 ubuntu
