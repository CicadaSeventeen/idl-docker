# idl-docker
A docker container to run idl. Based on Rockylinux8

docker hub site:
https://hub.docker.com/repository/docker/djypku/idl
https://hub.docker.com/repository/docker/djypku/idlprerun

Using distrobox is recommended.see
https://github.com/89luca89/distrobox


Usage:
1.
In bash shell running

```
tem1=`ifconfig|grep enp`
tem2=${tem1%%:*}
sudo ifconfig $tem2 hw ether 00:14:C2:3D:6E:AC
unset tem1
unset tem2
```
If somehow cannot install `ifconfig`,maybe you need to do is ONE of two options here
a. Using docker or podman to run [djypku/idlprerun](https://hub.docker.com/repository/docker/djypku/idlprerun) with `sudo`. The container will automatically exit.
b. Running that
```
tem1=`ifconfig|grep enp`
tem2=${tem1%%:*}
sudo ip link set dev $tem2 down
sudo ip link set dev $tem2 address 00:14:C2:3D:6E:AC
sudo ip link set dev $tem2 up
```
2.
Then
```
docker pull djypku/idl
distrobox create -i djypku/idl -n idl
distrobox enter idl
```
3.
Then in container
```
lmgrd
```
Then use `idlde` to use it.

After using it. Please stop the conainter or it will use up to 100% of one cpu core.

You have to repeat step 1 every time you reboot.

podman can also work for it,

