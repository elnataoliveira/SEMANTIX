### install docker
``` sh
sudo apt update -y
sudo apt install apt-transport-https ca-certificates curl
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt update -y
sudo apt install docker-ce docker-ce-cli containerd.io
sudo reboot
```
### install docker-compose

``` sh
sudo curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

### init cluster

``` sh
git clone https://github.com/rodrigo-reboucas/docker-bigdata.git
cd docker-bigdata/
docker-compose pull
docker-compose up -d
docker-compose --help
```
### basics commands

``` sh
docker ps
docker-compose logs namenode
docker logs namenode
docker --help
docker -it namenode bash
docker exec -it namenode bash
docker exec -it namenode ls
docker-compose stop
docker-compose start
docker-compose down 
docker volume prune
docker system prune -all
docker exec -t container command
docker cp diretorio container:/diretorio
docker exec -it namenode bash
docker exec -it hive-server bash
```
