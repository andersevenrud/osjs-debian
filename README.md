# osjs-debian

This repository builds a `.deb` package and `.iso` live image for Debian Buster.

**Currently only produces host architecture builds and is only intended for experimentation**

## Requirements

You only need docker.

## Usage

Build files and output files are located in `build/`.

First you have to create the base image that contains all tools to build:

```
# This is only performed once to create a local Docker imag
$ docker build -t osjs/debian .
```

Then use one of the following build scripts:

> NOTE: Builds are always fresh. Temporary files between runs are removed.

```
# Build debian package
$ docker run -v "${PWD}:/usr/src/osjs" osjs/debian ./build.sh

# Build live ISO image
$ docker run --privileged -v "${PWD}:/usr/src/osjs" osjs/debian ./image.sh
```

## Builds

Brief overview of the build results:

### Debian package

Contains the following:

* systemd service for the server
* systemd service for the X11 server
* electron launcher
* server with PAM authentication
* client without sources

### Live image

A Debian Buster live image (based on standard image) that has the debian package installed.

## Links

- https://github.com/os-js/OS.js
- https://www.devdungeon.com/content/debian-package-tutorial-dpkgdeb
- https://live-team.pages.debian.net/live-manual/html/live-manual/index.en.html
