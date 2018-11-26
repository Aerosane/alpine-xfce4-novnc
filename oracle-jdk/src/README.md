# Oracle Java [![](https://images.microbadger.com/badges/image/airdock/oracle-jdk:latest.svg)](https://microbadger.com/images/airdock/oracle-jdk:latest "Get your own image badge on microbadger.com")

Docker Image for Oracle Java SDK (JDK and JRE) based on airdock/base:jessie

This repository contains **Dockerfile** for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/airdock/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).

**Dependency**: airdock/base:jessie

**Few links**:

 - [Docker Java Image](https://github.com/dockerfile/java)

## Supported Version

%README_VERSION%


## Usage

You should have already install [Docker](https://www.docker.com/).

Execute:

	'docker run -t -i  airdock/oracle-jdk:latest java -version'

Please note that a correct docker command should be something like this one (using java user defined):

```
 CMD [ "gosu", "java:java", "/srv/java/jvm/bin/java", ... ]
```

JVM uses only 1/4 of system memory by default, with script java-dynamic-memory-opts,
you could set a specific percent of memory (80 % per default) :

```
 CMD [ "gosu", "java:java", "/srv/java/jvm/bin/java", "$(/srv/java/java-dynamic-memory-opts)", ... ]
 or
 CMD [ "gosu", "java:java", "/srv/java/jvm/bin/java", "$(/srv/java/java-dynamic-memory-opts 90)", ... ]
```
If you using this script take care of your host sizing.


## Change Log

### latest
- update image layer badge
- fix root image to airdock/base:jessie

### 1.2

- add JRE version
- JAVA HOME is bellow /srv/java/jdk or /srv/java/jre
- add shorlink /srv/java/jvm to simplify command line and absolute path

### 1.1

- add specific tag on SDK version
- add build process to generate all JDK version target
- add JAVA_HOME/bin in PATH, java-dynamic-memory-opts utility script for all version
- Use tarball from Oracle in order to install JDK
- JAVA HOME is bellow /srv/java/jdk

### 1.0

- add JAVA_HOME/bin in PATH
- add java-dynamic-memory-opts utility script (on 1.8 and latest version only)
- add webupd8team key
- add oracle jdk 8 and jdk 7
- declare JAVA_HOME
- use MIT license


## Build

You should install "make" utility.

Under each project, you could retrieve a Makefile with a set of *tasks*:

- **all**: alias to 'build'
- **clean**: remove all container which depends on this image, and remove image previously builded
- **build**: clean and build the current version
- **tag_latest**: tag current version with ":latest"
- **release**: build and execute tag_latest, push image onto registry, and tag git repository
- **debug**: launch an interactive shell using this image
- **run**: run image as daemon and print IP address.
- **save**: export docker image as a tar.gz file

See [Docker Project Tree](https://github.com/airdock-io/docker-base/wiki/Docker-Project-Tree) for more details.


## MIT License

```
The MIT License (MIT)

Copyright (c) 2015 Airdock.io

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
 ```
