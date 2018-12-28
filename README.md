# docker-utils

### Command line related
```
# Stop all containers
docker stop $(docker ps -a -q);

# Remove all containers
docker rm $(docker ps -a -q);

# Remove all images
docker rmi $(docker images -q);
```

### Shell-alias related
```
# Get container process
alias dps="docker ps"

# Get container IP
alias dip="docker inspect --format '{{ .NetworkSettings.IPAddress }}'"

# Stop all containers
dst() { docker stop $(docker ps -a -q); }

# Remove all containers
drm() { docker rm $(docker ps -a -q); }

# Remove all images
dri() { docker rmi $(docker images -q); }

# Show all alias related docker
dalias() { alias | grep 'docker' | sed "s/^\([^=]*\)=\(.*\)/\1 => \2/"| sed "s/['|\']//g" | sort; }

# Bash into running container
dbash() { docker exec -it $(docker ps -aqf "name=$1") bash; }

# Sh into running container
dsh() { docker exec -it $(docker ps -aqf "name=$1") sh; }
```
