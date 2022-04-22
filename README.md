# Creazione ambiente per collaudo swarm 

Crea in locale tutte le immagini docker-locale/docker necessarie

## Lanciare compose

docker-compose up -d

# Creazione shared fs

https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-18-04

In host
mkdir /srv/shared
sudo chown nobody:nogroup /srv/shared
sudo vim /etc/exports
/srv/shared    172.22.0.5(rw,sync,no_subtree_check)
/srv/shared    172.22.0.6(rw,sync,no_subtree_check)
/srv/shared    172.22.0.7(rw,sync,no_subtree_check)

sudo systemctl restart nfs-kernel-server

In client
sudo apt update
sudo apt install nfs-common 
( apt update && apt install nfs-common -y )

sudo mkdir /srv/shared
sudo chown nobody:nogroup /srv/shared

sudo mount <HOST-IP-ADDRESS>:/srv/shared /srv/shared
( sudo mount 172.21.186.224:/srv/shared /srv/shared )


