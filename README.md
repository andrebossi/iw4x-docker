# iw4x server

[![GitHub](https://badgen.net/badge/icon/github?icon=github&label)](https://github.com/andrebossi/iw4x-docker)
[![GitHub](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![GitHub Workflow Status](https://github.com/andrebossi/iw4x-docker/actions/workflows/docker-publish.yml/badge.svg)](https://github.com/andrebossi/iw4x-docker/actions/workflows/docker-publish.yml)

Container based on Wine and Alpine to run iw4x dedicated server.

## Getting Started

These instructions will cover usage information and for the Docker container.

### Prerequisities

In order to run this container you'll need [Docker](https://docs.docker.com/get-started/) and [docker-compose](https://docs.docker.com/compose/) installed.

Download server files at [Download page](https://dss0.cc/alterwarez/index.html) (Select Dedi files for iw4x) extract files in folder data.

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
```

### Usage

#### Run

Start server with docker-compose:

```sh
docker-compose up -d
```

Or run direct container:

```sh
docker container run -d --rm \
  --name iw4x-server \
  -v ./data:/iw4x/server/ \
  -e IW4X_ARGS: "-dedicated +set fs_game mods/bots +set sv_lanonly 1 +set net_port 28960 +exec serverlan.cfg +map_rotate" \
  -p 28960:28960 -p 28960:28960/udp \
  --restart always \
  iw4x-server
```

#### Resources

Read the [wiki](https://github.com/Jawesome99/IW4x/wiki/Server) for a complete setup.

#### Environment Variables

* `IW4X_ARGS` - Arguments for starting the server.
* `WINEARCH` - Wine architecture for configuring server default is win32.
* `LANG` - Lang to configure container.

#### Volumes
* `/iw4x/server/` - directory for server files.

## Built With

* [Wine](https://www.winehq.org/)
* [iw4x](https://iw4x.tumblr.com/post/161974206329/install-iw4x)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.