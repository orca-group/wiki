# Instance Setup

> This guide details the very easy process of setting up a Spacebin server instance.

This is a quick guide on how to setup a basic spacebin API instance.

There are two methods for installing the Spacebin Spirit server:

## Docker (recommended)

**Prerequisites:**

* [Git](https://git-scm.org/downloads)
* [Docker](https://www.docker.com/get-started)
* [`sudo`](https://www.sudo.ws/sudo/)


### Download the Git repository

These two commands will download the Git repository from Github and `cd` into that directory.

```command
$ git clone https://github.com/spacebin-org/spirit.git
$ cd spirit
```

### Build and run the docker image

These two commands will build a docker image called `spacebin-server` and run the docker image on port `80`.

```command
$ sudo docker build -t spacebin-server .
$ sudo docker run -d -p 80:9000 spacebin-server
```

## Manual

Documentation unwritten...
