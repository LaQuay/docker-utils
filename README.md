# docker-utils

### CLI related

#### Stop all containers
```docker stop $(docker ps -a -q);```

#### Remove all containers
```docker rm $(docker ps -a -q);```

#### Remove all images
```docker rmi $(docker images -q);```

### Shell-alias related

#### Get container process
```alias dps="docker ps"```

#### Get container IP
```alias dip="docker inspect --format '{{ .NetworkSettings.IPAddress }}'"```

#### Stop all containers
```dst() { docker stop $(docker ps -a -q); }```

#### Remove all containers
```drm() { docker rm $(docker ps -a -q); }```

#### Remove all images
```dri() { docker rmi $(docker images -q); }```

#### Log a container
Should pass the name, e.g.: *dlog container_1*

```alias dlog="docker logs $1"```

#### Log and follow a container
Should pass the name, e.g.: *dlog container_1*

```alias dlogf="docker logs -f $1"```

#### Sh into running container
Should pass the name, e.g.: *dsh container_1*

```dsh() { docker exec -it $(docker ps -aqf "name=$1") sh; }```

#### Bash into running container
Should pass the name, e.g.: *dbash container_1*

```dbash() { docker exec -it $(docker ps -aqf "name=$1") bash; }```
