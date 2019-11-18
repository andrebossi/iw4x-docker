# iw4x server

container based on wine and alpine to run iw4x server

## Getting Started

These instructions will cover usage information and for the Docker container.

### Prerequisities

In order to run this container you'll need [Docker](https://docs.docker.com/get-started/) and [docker-compose](https://docs.docker.com/compose/) installed.

Download server files at [Download page](https://dss0.cc/alterwarez/index.html) (Select Dedi files for iw4x) put files in ./data

### Installing

Pull the image from the Docker repository:

```sh
docker pull dobolinux/iw4x-server
docker tag dobolinux/iw4x-server iw4x-server
docker rmi dobolinux/iw4x-server
```

Or build the image from source:

```sh
git clone https://github.com/dobolinux/iw4x-docker.git iw4x-docker
cd iw4x-docker
docker-compose build --compress --force-rm --no-cache --pull
docker-compose up -d
```