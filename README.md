# Cara-Install-Docker-di-STB dan Install Packet Stream

```
wget https://download.docker.com/linux/debian/gpg
```

```
apt-key add gpg
```

```
nano /etc/apt/sources.list.d/docker.list
```

```
deb [arch=arm64] https://download.docker.com/linux/debian buster stable
```
Untuk versi Ubuntu Bionic
```
deb [arch=arm64] https://download.docker.com/linux/ubuntu bionic stable
```

## Langkah Berikutnya install Docker Container di STB Armbian

```
apt-get update && upgrade -y
```

```
apt-get install docker-ce -y
```

## check docker status
```
systemctl status docker
```
Tutorial Cek https://www.youtube.com/watch?v=Y5uO5aYt9Ng
## Untuk Cek Images Docker nya, ketik :
```
docker images
```
## Tambahan : Cara Install packet stream di stb
```
sudo docker stop watchtower && sudo docker rm watchtower && sudo docker rmi containrrr/watchtower && sudo docker stop psclient && sudo docker rm psclient && sudo docker rmi packetstream/psclient 
sudo docker run -d --restart=always -e CID=6IJl --name psclient1 packetstream/psclient:latest && sudo docker run -d --restart=always --name watchtower -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --cleanup --include-stopped --include-restarting --revive-stopped --interval 60 psclient
```
### Untuk Cek images Dockernya
```
docker images
```
### Cek lebih rinci lagi
```
docker ps -a
```
### Untuk Cek Packet Stream Sedang Berjalan 
```
docker logs KODENAMACONTAINER
```

# Step 1 – Remove Docker images, containers, and volumes
To completely remove Docker from your system, you'll need to remove any images, containers, and volumes that were created. To do this, use the following commands:

## Remove unused data
```
docker system prune --all --volumes
```

## Remove all services
docker service rm $(docker service ls -q)

## Remove all containers
docker rm -f $(docker ps -aq)

## Remove all images
docker rmi -f $(docker images -aq)

## Remove all volumes
docker volume rm $(docker volume ls -q)
Remove all data created and managed by Docker.
Step 2 – Stop Docker service
Before removing Docker from your system, you should stop the Docker service by running the following command:

systemctl stop docker
Shut down Docker.
This will ensure that Docker is not running in the background while you're removing it. 😉

# Step 3 – Uninstall Docker
It's now time to remove Docker from the operating system. Run the followings commands:

## Uninstalls the Docker Community Edition (docker-ce) package from your Debian system
apt-get purge docker-ce -y

## Removes any remaining Docker packages and their dependencies that were not automatically removed by the previous command
apt-get autoremove --purge docker-ce -y
Uninstall Docker without prompts.
This will remove any packages that were installed as dependencies of Docker but are no longer needed.

# Step 5 – Remove Docker group (optional)
If you had previously added users to the Docker users group to allow them to run Docker commands without sudo, you may want to remove the Docker group as well. Use the following command:

groupdel docker
This command will also remove the docker group from all users.
Step 4 – Remove Docker directories
Next, you'll need to remove any directories associated with Docker, including its configuration files and its storage location. Use the following commands:

## Remove the Docker configuration files
rm -rf /etc/docker

## Remove the Docker Daemon's storage location
rm -rf /var/lib/docker
