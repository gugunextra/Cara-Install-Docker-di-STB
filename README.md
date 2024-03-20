# Cara-Install-Docker-di-STB

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
apt-get update -y
```

```
apt-get upgrade -y
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

