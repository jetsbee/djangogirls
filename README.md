# Django girls tutorial with docker compose

- [Tutorial link](https://tutorial.djangogirls.org)
- [Docker compose samples](https://docs.docker.com/compose/samples-for-compose/#samples-tailored-to-demo-compose)

# Code styles

- Linter: flake8
- Formatter: black
- Import statement organizer: isort

## Start services

```sh
docker compose up
```

## Shut down services (Another shell)

```sh
docker compose down
```

## Create the Django project by running the docker compose run command as follows.

```sh
docker compose run web django-admin startproject mysite .
```
