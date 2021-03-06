# netty-hello-world

This project was created to understand the behavior of netty's included SO and to determine if its realistic to consider it a potential threat vector.


MD5 https://repo1.maven.org/maven2/io/netty/netty-all/4.1.65.Final/netty-all-4.1.65.Final.jar.md5

`6b1836a9748a74a68fb48e9151006c2f`


## Binary contents of netty-all-4.1.65.Final.jar

```
r631946@TRG529595 netty-all-4.1.65.Final % find . -name "*.so"
./META-INF/native/libnetty_transport_native_epoll_x86_64.so
./META-INF/native/libnetty_transport_native_epoll_aarch_64.so
```

## MD5 hashes for these files
```
MD5 (./META-INF/native/libnetty_transport_native_epoll_x86_64.so) = 58ef1e4ec1651598016d43a735c7feaa
MD5 (./META-INF/native/libnetty_transport_native_epoll_aarch_64.so) = ae34785c2d64ad58a40ae7958336b524
```

## building
`gradle build`

## running the jar
`java -jar build/libs/netty-hello-world-all.jar`

## testing that the server is running
```
% curl localhost:8088
Hello World from Clay's Netty Server!%     
```
## building the docker container
`docker build -t claytantor/netty-hello-world:latest .`

## running the netty server from docker container
`docker run -p 8088:8088 claytantor/netty-hello-world:latest`

## running a root shell on the docker container
```
% docker ps
CONTAINER ID        IMAGE                                 COMMAND                CREATED             STATUS              PORTS                  NAMES
75b785829378        claytantor/netty-hello-world:latest   "java -jar /app.jar"   8 seconds ago       Up 7 seconds        0.0.0.0:8088->8088/tcp   festive_wilbur

% docker exec -it festive_wilbur /bin/sh
/ # ls -al /tmp
total 12
drwxrwxrwt    1 root     root          4096 Jul 14 17:23 .
drwxr-xr-x    1 root     root          4096 Jul 14 17:23 ..
drwxr-xr-x    2 root     root          4096 Jul 14 17:23 hsperfdata_root
```