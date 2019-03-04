# docker-utils

## Tricks

### .dockerignore

Before the docker CLI sends the context to the docker daemon, it looks for a file named .dockerignore in the root directory of the context. If this file exists, the CLI modifies the context to exclude files and directories that match patterns in it.

### Example in Python dockerization
```
_env
.git
```

### Example in React dockerization
```
node_modules
deploy
build
.git
```
[Docker Documentation about .dockerignore](https://docs.docker.com/engine/reference/builder/#dockerignore-file)

## CLI related

### Stop all containers
```docker stop $(docker ps -a -q);```

### Remove all containers
```docker rm $(docker ps -a -q);```

### Remove all images
```docker rmi $(docker images -q);```

## Shell-alias related

### Get container process
```alias dps="docker ps"```

### Get container IP
```alias dip="docker inspect --format '{{ .NetworkSettings.IPAddress }}'"```

### Stop all containers
```dst() { docker stop $(docker ps -a -q); }```

### Remove all containers
```drm() { docker rm $(docker ps -a -q); }```

### Remove all images
```dri() { docker rmi $(docker images -q); }```

### Log a container
Should pass the name, e.g.: *dlog container_1*

```alias dlog="docker logs $1"```

### Log and follow a container
Should pass the name, e.g.: *dlogf container_1*

```alias dlogf="docker logs -f $1"```

### Sh into running container
Should pass the name, e.g.: *dsh container_1*

```dsh() { docker exec -it $(docker ps -aqf "name=$1") sh; }```

### Bash into running container
Should pass the name, e.g.: *dbash container_1*

```dbash() { docker exec -it $(docker ps -aqf "name=$1") bash; }```
