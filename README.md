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
