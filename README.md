# docker-cygno-mc
Requisites:
* Linux: Docker packages
* Windows: Docker desktop and X11 server installed and running (for example XMing)


## Download image
To download image from command line
```
docker pull ghcr.io/gdimperi/docker-cygno-mc/cygno-mc:v1
```

## Run container

### Linux 
```
sudo docker run -it --net=host --env="DISPLAY" --volume="$HOME/.Xauthority:/root/.Xauthority:rw"  ghcr.io/gdimperi/docker-cygno-mc/cygno-mc:v1
```

### Windows

In Windows command prompt (you can run the command prompt from the Docker Desktop app)
```
set DISPLAY host.docker.internal:0
docker run -it --rm  -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix ghcr.io/gdimperi/docker-cygno-mc/cygno-mc:v1 sh
```
Or you can use the bash shell of linux subsystem (Ubuntu on Linux)
```
docker run -it --rm  -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix ghcr.io/gdimperi/docker-cygno-mc/cygno-mc:v1 sh
```
## Run CYGNO-MC Geant4 application

```
su geant4user
source ~/setup.sh
cd ~/CYGNO-MC-build-cygno_04
g4cmake ../CYGNO-MC
make
./CYGNO
```
