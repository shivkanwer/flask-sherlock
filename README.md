# Sherlock

Welcome to Sherlock project. Sherlock is a movie recommendation microservice written in Flask.

Below steps can be executed on any unix like system.

## Setup SSH key

**This step is option and can be omitted.**

Create ssh key and add it to GitHub's [SSH keys](https://github.com/settings/keys) settings.

```bash
ssh-keygen
cat ~/.ssh/id_rsa.pub
```

## Installation

```bash
# Cloning the source code
git clone https://github.com/ldynia/flask-sherlock.git
cd flask-sherlock

# Building and running docker container
docker build --tag flask-sherlock --build-arg FLASK_DEBUG=True .
docker run --detach --name sherlock --publish 80:8080 --rm flask-sherlock
docker ps
```

## API

Filter up algorithm
```bash
curl "http://localhost/api/v1/movies/recommend?title=Kingpin"
curl "http://localhost/api/v1/movies/recommend?title=Lost%20in%20Translation"
```

## Testing

Unit test
```bash
docker exec sherlock pytest
```

Code coverage
```bash
docker exec sherlock coverage run -m pytest
docker exec sherlock coverage report
```

Stop container
```bash
docker stop sherlock
```
