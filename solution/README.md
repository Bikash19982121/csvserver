1) Create a project directory
     mkdir project-cloudinfra
     cd project-cloudinfra/
2) Check if docker and docker-compose are installed:
     docker version
     docker-compose version
3) Pull the specified docker images:
     docker pull infracloudio/csvserver:latest
     docker pull prom/prometheus:v2.22.0
4) Clone the specified repo:
     git clone https://github.com/infracloudio/csvserver.git
5) List the pulled docker images:
     docker images
6) Run the docker container:
     docker run -d -i infracloudio/csvserver:latest	
7) Check if the docker container is running or not.
     docker ps
8) If the docker container is not running, check the status
     docker ps -a
9) Check the logs and see what is the error:
     docker logs <container-id>
2021/09/21 08:21:37 error while reading the file "/csvserver/inputdata": open /csvserver/inputdata: no such file or directory
10) Create a shell script to create the inputFile
#!/bin/bash
for i in {0..9}
do
   echo "$i, $RANDOM"; 
done > inputFile
11) Run the cotainer by mouting the inputfile path
    docker run -d -i -v F:/project-cloudinfra/csvserver/solution/inputFile:/csvserver/inputdata infracloudio/csvserver:latest
12) Login to the container
    docker exec -it <container-id> bash

13) Stop the running container
    docker stop <container-id>
14) Run the container and provide the port mapping
    docker run -d -i -v F:/project-cloudinfra/csvserver/solution/inputFile:/csvserver/inputdata -p 9393:9300 infracloudio/csvserver:latest
15) Stop the container
    docker stop <container-id>
16) Run again by specifying the environment variable
    docker run -d -i -v F:/project-cloudinfra/csvserver/solution/inputFile:/csvserver/inputdata -p 9393:9300 -e CSVSERVER_BORDER='Orange' infracloudio/csvserver:latest




