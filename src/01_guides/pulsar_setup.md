# Pulsar Setup

> This guide details the very easy process of setting up an instance of the Pulsar client for Spacebin.

This is a quick guide on how to install and setup an instance of Spacebin's official web client: Pulsar.

There are two methods for installing Pulsar:

## Docker (recommended)

**Prerequisites:**

* [Docker](https://www.docker.com/get-started)
* [`sudo`](https://www.sudo.ws/sudo/)
* An internet connection.

### 1. Pull and run the Docker image

Using this method the installation and execution of a Spirit instance is quite easy, and can be done with two commands:

```sh
# This will pull and run Docker image on Port 80
$ sudo docker pull spacebinorg/pulsar:v1.1.3
$ sudo docker run -d \
  --restart=always \
  --env PULSAR_INSTANCE="https://spaceb.in/" \
  -p 3000:80 \
  spacebinorg/pulsar:v1.1.3
```

You're done. Pulsar doesn't really have a configuration system, just a few environment variables, they are `PORT` and `PULSAR_INSTANCE`.

Right now, the `PULSAR_INSTANCE` environment variable is the only required one and is used to set the Spirit instance which Pulsar will serve as the client for.

## Manual

Instructions unfinished.
