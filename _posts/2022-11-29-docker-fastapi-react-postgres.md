---
layout: single
title: "Using docker with FastAPI, React & PostgreSQL"
header:
  overlay_color: "#333"
tags:
  - docker
  - react
  - fastapi
  - postgresql
---

I need to come up with a Docker solution for my current development needs. 

[Docker](https://www.docker.com/) containerizes your app, so you can use them independent of your development environment or something. I'm going to base this on the following article by [Pete Jadhav](https://petejadhav.github.io/fastapi-react-docker/). Lets see what happens!

Going to need a [Docker-Compose](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-install-Docker-and-docker-compose-on-Ubuntu) file that sums how to combine all the docker images. This should be in the `parent directory`. 

~~~docker
services:
    db:
        build: postgres_db
        healthcheck:
            test: ["CMD", "pg_isready", "-q", "-d", "${POSTGRES_DB}", "-U", "postgres"]
    
    web:
        build: frontend
        ports:
            - 80:80
        depends_on:
            - api
    api:
        build: backend
        environment:
            - PORT=80
            - DB_HOST=db
        depends_on:
            db:
                condition: service_healthy
~~~

To start all these services, run:

~~~
docker-compose up --build
~~~

To be continued...