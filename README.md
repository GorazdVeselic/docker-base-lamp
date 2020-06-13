# Base docker setup for LAMP

### Installation

This project requires [Docker](https://www.docker.com/) to run.

Create new project root direcotry:
```sh
$ mkdir new_project
$ cd new_project
```

Clone this repo into newly created direcotry:
```sh
$ git clone git@github.com:GorazdVeselic/docker-base-lamp.git .
```

Move to .docker folder and run docker compose up command to start containers in deamon mode:
```sh
$ cd .docker
$ docker-compose up -d
```

Put index.php file with some HTML code in '/new_project/src/' folder 
```sh
cd ..
cd src
touch index.php
echo "Hello world" >> index.php
```
