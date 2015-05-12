# zeitgeist/docker-claws

[Claws Mail](http://www.claws-mail.org/) (latest version) in a Docker container.

## Requirements

* [Docker](https://www.docker.com/) 1.6+ (previous versions may work fine, but I haven't tried)
* An X11 socket

## Installation

Get the [trusted build on the docker hub](https://registry.hub.docker.com/u/zeitgeist/docker-claws/):

```bash
$ docker pull zeitgeist/docker-claws
```

or download and compile the source yourself from Github:

```bash
$ git clone https://github.com/alexzeitgeist/docker-claws.git
$ cd docker-claws
$ docker build -t zeitgeist/docker-claws .
```

## Usage

```bash
$ docker run --rm \
  -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
  -e DISPLAY=unix$DISPLAY \
  zeitgeist/docker-claws
```

With persistent storage for settings and mail:

Create a folder, e.g. ${HOME}/claws. Then map it like this:

```bash
$ docker run --rm \
  -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
  -e DISPLAY=unix$DISPLAY \
  -v "${HOME}/claws":"/home/user" \
  zeitgeist/docker-claws
```
