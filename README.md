# Docker best Practices
| Development                     | Production                          |
| ------------------------------- | --------------------------------------------- |
| Use bind mounts to give your container access to your source code.  | Use volumes to store container data. |
| Use Docker Desktop for Mac or Docker Desktop for Windows.  | Use Docker Engine, if possible with userns mapping for greater isolation of Docker processes from host processes. |
| Don’t worry about time drift. | Always run an NTP client on the Docker host and within each container process and sync them all to the same NTP server. If you use swarm services, also ensure that each Docker node syncs its clocks to the same time source as the containers. |

```
How to use .dockerignore its like .gitignore

Let’s look at an example of .dockerignore file.

passphrase.txt
logs/
.git
*.md
.cache

```


## What is difference between COPY and ADD.
According to the Dockerfile best practices guide, we should always prefer COPY over ADD unless we specifically need one of the two additional features of ADD.
```
COPY - 99% of the time you should be using COPY
     COPY doesn't support <src> with URL scheme.
     COPY doesn't unpack compression file.
  
ADD - add recommended only below conditions
    ADD http://someserver.com/filename.pdf /var/www/html   # URL's
    ADD http://example.com/big.tar.xz /usr/src/things/     # Tar files
  ```  
 The ADD directive will automatically expand tar files into the image file system. While this can reduce the number of Dockerfile steps required to build an image, it may not be desired in all cases
############################################

  
  # What is difference between CMD and Entrypoint
  ```
  ENTRYPOINT: 
     The ENTRYPOINT specifies a command that will always be executed when the container starts.
  
  CMD: 
     The CMD specifies arguments that will be fed to the ENTRYPOINT
     =====================================================
   docker run -d --name test01 --cpu-shares 512 schoolofdevops/stress --cpu 1
   ```
   ```
   Linking Containers
   docker run -itd --name redis redis:alpine
   docker run -itd -P --name vote --link redis:redis -P schoolofdevops/vote
   ```
Multistage Builds...
```
FROM schoolofdevops/maven:spring AS build
WORKDIR /app
COPY . .
RUN mvn package -Dmaven.test.skip
#RUN mvn package -DskipTests

FROM openjdk:8-alpine AS run
COPY --from=build /app/target/spring-petclinic-1.5.2.jar /run/petclinic.jar
EXPOSE 8080
CMD java -jar /run/petclinic.jar
```
A specific build from a multistage build..
```

## install docker-compose for ubuntu 20
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
