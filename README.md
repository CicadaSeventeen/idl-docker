# idl-docker
A docker container to run idl. Based on Rockylinux8

docker hub site:
https://hub.docker.com/repository/docker/djypku/idl
https://hub.docker.com/repository/docker/djypku/idlprerun

Using distrobox is recommended.see
https://github.com/89luca89/distrobox


Usage:
running

```
tem1=`ifconfig|grep enp`
tem2=${tem1%%:*}
sudo ifconfig $tem2 hw ether 00:14:C2:3D:6E:AC
unset tem1
unset tem2
```
If somehow cannot install `ifconfig`,maybe you need to do is
1. Using docker or podman to run [djypku/idlprerun](https://hub.docker.com/repository/docker/djypku/idlprerun) with root
Or
2. 

```
docker pull djypku/idl
distrobox create -i djypku/idl -n idl
distrobox enter idl
```
Then in container
```
lmgrd
dis 
```

podman can also work for it,

