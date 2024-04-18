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

## Synchronizes the database state with the current set of models and migrations. (Execute the SQL commands)

Ref. [migrate](https://docs.djangoproject.com/en/5.0/ref/django-admin/#migrate)

```sh
# By pecific app
python manage.py migrate <`APP_NAME`>

# All apps
python manage.py migrate
```


## Create new migrations based on the changes you have made to your django models. (Generate the SQL commands)

```sh
# By specific app
python manage.py makemigrations <`APP_NAME`>

# All apps
python manage.py makemigrations
```

## Create superuser for admin
```sh
python manage.py createsuperuser
```
