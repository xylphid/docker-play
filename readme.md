![Play! Framework](https://www.playframework.com/assets/images/logos/play_full_color.png)

# Play! Framework

## Supported tags

* `1`, `1.5`, `1.5.0` ([Dockerfile](https://github.com/xylphid/docker-play/blob/master/1/5/Dockerfile))
* `latest`, `1.5-slim`, `1.5.0-slim`, `1.5-slim-jdk11`, `1.5.0-slim-jdk11` ([Dockerfile](https://github.com/xylphid/docker-play/blob/master/1/5-slim/Dockerfile))
* `1.4`, `1.4.4` ([Dockerfile](https://github.com/xylphid/docker-play/blob/master/1/4/Dockerfile))
* `1.4-alpine`, `1.4.4-alpine` ([Dockerfile](https://github.com/xylphid/docker-play/blob/master/1/4-alpine/Dockerfile))

## How to use this image

### Mounting project

`$ docker run --name some-name -v /path/to/project:/app -d xylphid/play-framework:1`

### Exposing external port

`$ docker run --name some-name -v /path/to/projet:/app -p 80:9000 -d xylphid/play-framework:1`
Then you can hit `http://localhost/` or `http://host-ip`in your browser.

## How to compose with this image

    version: "3"
    services:
      app:
        image: xylphid/play-framework:1.4.4
        port:
          - "80:9000"
        restart: always
        volumes:
          - /path/to/project:/app

### Traefik configuration

    version: "3"
    services:
      app:
        image: xylphid/play-framework:1.4.4
        labels:
          - "traefik.backend=my-project"
          - "traefik.frontend.rule=Host:my-project.domain.tld"
          - "traefik.port=9000"
        restart: always
        volumes:
          - /path/to/project:/app

## Quick reference

* [Play! Framework](https://www.playframework.com/)
* [Documentation](https://www.playframework.com/documentation/1.4.x/home)

## Image inheritance

This docker image inherits from [openjdk:8](https://hub.docker.com/_/openjdk/) image.