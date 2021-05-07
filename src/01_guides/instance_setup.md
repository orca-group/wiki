# Instance Setup

> This guide details the very easy process of setting up a Spacebin server instance.

This is a quick guide on how to setup a basic Spacebin API instance.

There are two methods for installing the Spacebin Spirit server:

## Docker (recommended)

**Prerequisites:**

* [Docker](https://www.docker.com/get-started)
* [`sudo`](https://www.sudo.ws/sudo/)
* An internet connection.

### 1. Pull and run the Docker image

Using this method the installation and execution of a Spirit instance is quite easy, and can be done with two commands:

```sh
# This will pull and run Docker image on Port 80
$ sudo docker pull spacebinorg/spirit:v0.1.6a
$ sudo docker run -d -p 80:9000 spacebinorg/spirit:v0.1.6a
```

You're done. If you want to configure the Instance you're going to have use a somewhat-convoluted method due to a [parsing issue](https://github.com/spacebin-org/spirit/issues/239).

You need to use a [Docker volume](https://docs.docker.com/storage/volumes/) to replace the `/opt/spirit/config.toml` with a local file containing your instance's configuration. For more information on how to configure consult the [Config Options](../02_server/config_options.md) page of this wiki or the [Configuring Spirit](#2-configure-spirit) section on this page.

## Manual

* [Golang](https://www.golang.org/)
* [Magefile](https://magefile.org/)
* An internet connection.
* [Git](https://git-scm.com/)

### 1. Download the Git repository

These two commands will download the Git repository from Github and change into that directory.

```sh
$ git clone https://github.com/spacebin-org/spirit.git
$ cd spirit
```

### 2. Configure Spirit

You now need to configure your Spirit instance, so that it may run with settings that work best in your environment.

A full list of the options available in the `config.toml` file are listed on the [Config Options](../02_server/config_options.md) page. Each setting comes with a default that we at the Spacebin Team find reasonable.

We're working on creating more in-depth instructions for configuring an instance, but until then you'll have to do with this. Although, we don't think it's very hard to configure Spirit.

There are currently two options you may use for configuring &mdash; environment-based and file-based. However, the only one of these options that currently works is the file-based approach as the other approach currently has a known issue with parsing some `_` delimited fields.

### 3. Build and run the binary

Now, you can try building the actual Spirit program. Since the application is written in Go, for any non-production environment we must build a binary for the program.

Thanks to our existing build system this can we be quite easily done, provided you've installed and setup [Magefile](https://magefile.org/).

**If you have, run the commands either `mage run` or `mage build`.** Either of these commands will build the Spirit program, however with the former option Mage will automatically run the binary after building it.

If you used instead the latter option you must now execute the `spirit` binary outputted by the program in the `bin/` folder of the project. Since each operating system has a different way of running the binary this guide will not go into depth on how to it should be ran.


