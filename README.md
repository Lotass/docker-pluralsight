# Docker Deep Dive

> Learning Docker with [Pluralsight course](https://app.pluralsight.com/library/courses/docker-deep-dive/description)

## Major Docker Components

### Images

Docker containers are launched from Docker images. i.e. image is a built-time concept, and containers are runtime.

For example, to launch an Ubuntu container and run a bash shell inside of it:

```shell
docker run -it ubuntu bash
```

`it` specifies interactive and terminal.

`ubuntu` specifies which image to base container on.

Sample output

```
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
5a132a7e7af1: Pull complete
fd2731e4c50c: Pull complete
28a2f68d1120: Pull complete
a3ed95caeb02: Pull complete
Digest: sha256:4e85ebe01d056b43955250bbac22bdb8734271122e3c78d21e55ee235fc6802d
Status: Downloaded newer image for ubuntu:latest
```

`Unable to find image 'ubuntu:latest' locally` Since this is the first time an ubuntu container is being launched, don't have a local copy, therefore it gets pulled from Docker Hub, which is the public Docker registry.

`5a132a7e7af1, fd2731e4c50c, etc.` Images are comprised of multiple layers, each number represents a layer (more details later in course).

`ubuntu:latest` On Docker hub, there are many different versions of ubuntu, if a version number is not specified as part of the `run` command, then Docker will grab the image that's tagged as the `latest` version.

Docker `pull` command is used to pull images from Docker hub and install them locally. Saves time when running containers, don't have to wait for download.

To pull all versions of an image (rather than just latest which is the default)

```shell
docker pull -a ubuntu
```

To list all the images locally

```shell
docker images ubuntu
```

IMAGE ID uniquely identifies each image. Note the same image can have multiple different tags.

Docker images contain all the data and metadata required to fire up a container.

### Containers
