## Docker-compose

##  env_file VS .env
```
.env     - The .env file feeds those environment variables only to your docker compose file, which in turn, can be passed to the containers as well.
env_file - But the env_file option only passes those variables to the containers and NOT the docker compose file 

[root@chop-rh8-01 webapp]# cat .env
TAG=v1.5

[root@chop-rh8-01 webapp]# cat docker-compose.yaml
services:
  webapp:
    env_file: env_vars
    image: nirulabs/tea:${TAG}  # It takes variable from .env file
    ports:
      - "8000:80"
    volumes:
      - "/data"

## docker-compose config output 
[root@chop-rh8-01 webapp]# docker-compose config
services:
  webapp:
    environment:
      ENVIRONMENT: PROD
    image: nirulabs/tea:v1.5
    ports:
    - published: 8000
      target: 80
    volumes:
    - /data
version: '3.9'


## env_file 
[root@chop-rh8-01 webapp]# cat docker-compose.yaml
services:
  webapp:
    env_file: env_vars
    image: nirulabs/tea
    ports:
      - "8000:80"
    volumes:
      - "/data"

## config output
[root@chop-rh8-01 webapp]# docker-compose config
services:
  webapp:
    environment:
      ENVIRONMENT: PROD # This variable is coming from env_vars file
    image: nirulabs/tea
    ports:
    - published: 8000
      target: 80
    volumes:
    - /data
version: '3.9'
```
## How to run docker-compose from a file..
## docker-compose docker-lemp.yaml up -d
```
[root@chop-rh8-01 docker-compose]# docker compose -f docker-lemp.yaml --dry-run up
 DRY-RUN MODE - Building image docker-compose-backend with buildkit
WARN[0000] Found orphan containers ([docker-compose_webapp_1]) for this project. If you removed or renamed this service in your compose file, 
you can run this command with the --remove-orphans flag to clean it up.
[+] Running 4/0
 ✔ DRY-RUN MODE -  Container docker-compose-mysql-1       Created                                                                                  0.0s
 ✔ DRY-RUN MODE -  Container docker-compose-phpmyadmin-1  Created                                                                                  0.0s
 ✔ DRY-RUN MODE -  Container docker-compose-backend-1     Created                                                                                  0.0s
 ✔ DRY-RUN MODE -  Container docker-compose-nginx-1       Created                                                                                  0.0s
[root@chop-rh8-01 docker-compose]#
```
