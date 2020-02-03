# Dockerzie Flask Application

---

## Docker Clash Course

``` bash
[start]
sudo systemctl start docker (debian based)
sudo service docker {stop|start|restart} (centos)

[build]
docker build -t whois-api:latest .

[List container]
docker ps -a  ## list all
docker ps -l ## list latest image

[List image]
docker image ls

[remove]
docker rmi -f $(docker images -f "dangling=true" -q) ## daggling images
```

## Docker Intro

- Make sure you have installed docker and docker-compose. Verify your
  installation by checking their version

- Add the `Dockerfile`

``` bash
## we choose alpine for the sake of tiny size
FROM python:3.7-alpine

RUN pip3 install gunicorn ## wsgi server in your container

## choose 'app' as workdir. Docker will create if it doesn't exists
WORKDIR /app

# copy just the requirements.txt first to leverage Docker cache
COPY ./requirements.txt /app/requirements.txt
RUN pip3 install -r /app/requirements.txt

COPY . /app

## define the port you will be using
EXPOSE 5000
```

Read [Dockerfilereference](https://docs.docker.com/engine/reference/builder/#from) documentation to learn more about these keywords.

To learn more about `Alpine OS` apk command read [Alpine Linux package management wiki](https://wiki.alpinelinux.org/wiki/Alpine_Linux_package_management).

Leveraging Docker build cache documented in [Dockerfile Bestpractice](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#leverage-build-cache)

## Build the image

``` bash
docker build -t flask-tutorial:0.0.1 .
```
- `-t`: to tag your image name <image-name:tag>
- `.` : current dir (bash syntax)

## Running the container

For the sake of ease, we will use `docker-compose` to run the container.

!!! Note

    Please discuss with your team, what port you will be using and what OS
    variable that you need (if you use `environment` keyword)

Then, add the appropriate `docker-compose.yml` file:

``` yaml
## remove anyline like this, I am just a description

version: '3'
services:
  whois: ## your container name
    image: flask-tutorial:0.0.1 ## your image name (that you built earlier) with the tag
    ports: ## the port on your `HOST:CONTAINER`
        - "5000:5000"
    environment: ## discuss with your team what to put here
      - APP_HOST=0.0.0.0
      - APP_PORT=5000
      - WHOIS_KEY=fakekey123
    command: sh run.sh server production
```

Read [Docker Compose](https://docs.docker.com/compose/compose-file/#ports)
documentation to learn more about these keyword.

Run the app when everything ok

`$ docker-compose up`
