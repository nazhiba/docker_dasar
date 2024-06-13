# youtube source
https://www.youtube.com/watch?v=3_yxVjV88Zk&t=1639s


# cloud learn docker
https://labs.play-with-docker.com/


DOCKER COMMAND

# Cek Versi Docker
docker --version

# Menampilkan image Docker
docker image ls

# Install Image Docker
docker pull []:[]

#Menampilkan semua container docker
docker container ls -a

# Menampilkan container docker yang aktif
docker container ls

# membuat container
docker container create --name inicontoh redis:latest

# menjalankan container
docker container start inicontoh

# stop container
docker container stop inicontoh

# hapus container
docker container rm inicontoh

# container log
docker container logs contoh
docker container logs - f contoh
1 [12828]

# container exec
-masuk container
docker container exec -i -t contoh /bin/bash
-keluar
exit

# container port
-penggunaan port forwarding
docker container create --name nginxservernadzib --publish 8080:80 nginx:latest

disini dibuat container baru dengan image nginx:latest dengan port default contanier 80 lalu kita forward ke 8080 di komputer lokal kita

ping dengan command 
ping [localhost]:[port]
default localhost adalah 127.0.0.1 dengan port yang kita forward tadi ke port 8080
jadi
ping 127.0.0.1:8080

sudo netstat -tuln

# container env
docker container create --name mongonadzib2 --publish 27017:27017 --env ME_CONFIG_MONGODB_ADMINUSERNAME=nazhiba --env ME_CONFIG_MONGODB_ADMINPASSWORD=nazhiba mongo:latest

# Container stats
docker container stats

# Container resource limit
docker container create --name kancilnginx --memory 100m --cpus 0.9 --publish 8089:80 nginx:latest

# Parameter Mount [sudah tidak direkomendasikan]
docker container create --name dataku --memory 200m --cpus 3 --publish 27080:27017 --env ME_CONFIG_MONGODB_ADMINUSERNAME=kali --env ME_CONFIG_MONGODB_ADMINPASSWORD=sijitekan8 --mount "type=bind,source=/root/data_penting,destination=/data/db" mongo:latest

# List Volume
docker volume ls

# Membuat Volume
docker volume create nazhibacloud

# Menghapus Docker Volume
docker volume rm nazhibacloud

# Container Volume
 docker container create --name nazhibamongo --mount "type=volume,source=nazhibacloud,destination=/data/db" --publish 27900:27017 --env ME_CONFIG_MONGODB_ADMINUSERNAME=kali --env ME_CONFIG_MONGODB_ADMINPASSWORD=sijitekan8 mongo:latest

# Backup Volume
docker container run --rm --name nazhibaubuntu --mount "type=bind,source=/root/backup,destination=/backup" --mount "type=volume,source=nazhibacloud,destination=/data" ubuntu:latest tar cvf /backup/nazhiba_backup.tar.gz /data

# Restore Volume
docker container run --rm --name nazhibaubuntu --mount "type=bind,source=/root/backup,destination=/backup" --mount "type=volume,source=nadzibrestore,destination=/data" ubuntu:latest bash -c "cd data && tar xvf /backup/nazhiba_backup.tar.gz --strip 1"

# List Docker Network
docker network ls

# Docker Network

-bridge
docker network create --driver bridge examplenetwork
-host
-none

# Hapus Docker Network
docker network rm examplenetwork

# Koneksi Container ke Network
docker container create --name nginx_server --network jaringan_container nginx:latest

# docker container create --name
redis_server2 --network jaringan_container redis:latest

# Hapus Container dari Network
docker network disconnect jaringan_container redis_server2

# Menambahkan Cointaner ke Netowk
docker network connect jaringan_container redis_server2

# Inspect
docker image inspect redis:latest
docker container inspect redisserver
docker volume inspect nadzibcloud
docker network inspect nadzibnet


# prune
hapus container otomatis
docker container prune
docker image prune
docker network prune
docker volume prune
docker system prune hapus container. image, dan network yang sudah tidak digunakan


