# Intro docker

[Main site](https://www.docker.com/)

[Docker Documentation](https://docs.docker.com/)

## How to install docker to ubuntu server:

```bash
sudo apt-get install docker
```

## How to start docker server:

```bash
sudo systemctl start docker
```

## How to install docker-compose:

```bash
pip install docker-compose
```

## Example Dockerfile
```Dockefile
FROM python:3.8-slim-buster

WORKDIR /app
```

## Example docker-compose.yml
```yaml
version: '3'

services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/app
```

## How to build docker image:
```bash
docker build -t myapp .
```

## How to run docker container:
```bash
docker run -d -p 5000:5000 myapp
```

## How to list docker images:
```bash
docker images -a
```

## How to list docker containers:
```bash
docker ps -a
```

## How to remove all docker containers:
```bash
docker rm $(docker ps -a -q)
```

## How to remove all docker images:
```bash
docker rmi $(docker images -a -q)
```

## docker-compose with django app
```yaml
version: '3'

services:
  web:
    build: .
    command: python manage.py runserver
    ports:
      - "8000:8000"
    volumes:
        - .:/app
    depends_on:
        - db
  db:
    image: postgres
    environment:
        POSTGRES_DB: mydb
        POSTGRES_USER: myuser
        POSTGRES_PASSWORD: mypassword
  
  test:
    build: .
    command: python manage.py test
    volumes:
        - .:/app
    depends_on:
        - db
```

### How to use docker-compose with django app
```bash
docker-compose up
```

### How to stop docker-compose
```bash
docker-compose down
```

### How to run docker-compose in background
```bash
docker-compose up -d
```

### How to list docker-compose services
```bash
docker-compose ps
```

### How to run command in docker-compose service
```bash
docker-compose exec web python manage.py createsuperuser
```

### How to run tests in docker-compose service
```bash
docker-compose exec test
```

