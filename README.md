# Dock.sh

docker helper for developers

## TL;DR;
```
docker login

./dock pull
./dock run
```

### Installation instructions:

* Install docker
```
sudo apt-get install wget && wget -qO- https://get.docker.com/ | sh
sudo usermod -aG docker <username>
```
or use sudo before the dock commands

Mac OS
Connect your shell to the default machine.
```
$ eval "$(docker-machine env default)"
```

* Login to docker
```
docker login
```

* Download the last image, init db volume, start container.
```
sudo ./dock pull

sudo ./dock run
```

* Open localhost:3000 in the browser. Enjoy.

Max OS:
Use your internal IP for access like 192.168.99.100:3000

## Brief basic usage and description
There are images and containers.
You can think about image like as a binary program file.
And container is like a running copy of binary. So it is a one-to-many association.
Program container should be immutable, so data should be located in other - data-only container.

App docker image is a minimal system (Ubuntu xx.yy LTS) with own
`node`, `cron`, `ps`, `mongod`, `runit` process supervisor and even `sshd`.
In theory it can run at any x86-64 linux distribution (MacOS, Windows in virtualization).

There is a script `dock` for easy container management in development.
Project located at `/app`. Supervised startup script can be located at `/etc/service/`.

### Get latest version of image
```
./dock pull
```

### Run container:
Create and start container
```
./dock run
```
In development environment it will mount current local directory to /app inside container.

### Start shell inside running container:
```
./dock sh
```

### Run command inside running container:
```
./dock exec ps aux
```

### Start already created container:
```
./dock start
```

### Show logs:
Show container logs (-f for follow)
```
./dock logs
```

### Stop running container:
```
./dock stop
```

### Remove container:
```
./dock rm
```

### Build image from scratch:
```
./dock build
```

### Push image to repository:
```
./dock push
```
