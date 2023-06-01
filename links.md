## Linking in docker.
## Source: https://docs.docker.com/network/links/

```
Links allow containers to discover each other and securely transfer information about one container to another container. When you set up a link, 
you create a conduit between a source container and a recipient container. The recipient can then access select data about the source. 
To create a link, you use the --link flag. 
First, create a new container, this time one containing a database.
```
## DB container
```
## This creates a new container called db from the training/postgres image, which contains a PostgreSQL database.

docker run -d --name db training/postgres   ## Did you notice no port number exposed
```
## Web container
```
Now, create a new web container and link it with your db container.
docker run -d -P --name web --link db:db training/webapp python app.py   # -P will create random port

[root@homelab]# docker ps
CONTAINER ID   IMAGE               COMMAND                  CREATED          STATUS          PORTS                                         NAMES
81ce20b257bf   training/webapp     "python app.py"          9 minutes ago    Up 9 minutes    0.0.0.0:32768->5000/tcp, :::32768->5000/tcp   web
d51ff6a84cf8   training/postgres   "su postgres -c '/us…"   11 minutes ago   Up 11 minutes   5432/tcp                                      db


This links the new web container with the db container you created earlier. The --link flag takes the form:
```
## web container can ping DB container, but db container cant ping web container
```
[root@homelab]# docker exec -it web bash
root@81ce20b257bf:/opt/webapp# ping db
PING db (172.17.0.2) 56(84) bytes of data.
64 bytes from db (172.17.0.2): icmp_seq=1 ttl=64 time=0.144 ms
64 bytes from db (172.17.0.2): icmp_seq=2 ttl=64 time=0.082 ms
64 bytes from db (172.17.0.2): icmp_seq=3 ttl=64 time=0.116 ms
64 bytes from db (172.17.0.2): icmp_seq=4 ttl=64 time=0.085 ms
64 bytes from db (172.17.0.2): icmp_seq=5 ttl=64 time=0.083 ms

Homelab#docker exec web ping db
PING db (172.17.0.2) 56(84) bytes of data.
64 bytes from db (172.17.0.2): icmp_seq=1 ttl=64 time=0.556 ms
64 bytes from db (172.17.0.2): icmp_seq=2 ttl=64 time=0.081 ms

Homelab#docker exec db ping web
ping: unknown host web

```
## How to verify Links..
```
Homelab#docker inspect -f "{{ .HostConfig.Links }}" web
[/db:/web/db]


```
