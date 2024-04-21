# Django girls tutorial with docker compose

- [Tutorial link](https://tutorial.djangogirls.org)
- [Docker compose samples](https://docs.docker.com/compose/samples-for-compose/#samples-tailored-to-demo-compose)

# Code styles

- Linter: flake8
- Formatter: black
- Import statement organizer: isort

## Install tailwindcss dependencies

```sh
npm install
```

## Watch tailwindcss

```sh
npm run dev
```

## Build tailwindcss

```sh
npm run build
```

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

## Run django interactive console

```sh
python manage.py shell
```

## Need to know

- n+1 문제 방지

```python
## Lazy loading (n+1 query excution)

# i.e
posts = Post.filter(pk__gt = 3)
for post in posts:
    post.comments.text

## Eager loading

# 1. select_related (Inner Join) <- 두 테이블간 join을 할 수 있는 구조에서 사용가능, 1:1, 1:N 에서 사용가능
# 2. prefetch_related <- 2개의 테이블을 각각 불러드려서, django내에서 합침, N:N 에서도 사용가능

# i.e (정방향 참조, 1:1 관계나 1:N 관계 중 N;Foreign Key를 정의하는 쪽이 사용)
comments = Comment.select_related(post).filter(pk__gt = 3)
for comment in comments:
    comment.post.author

# i.e (역방향 참조, M:N 관계나 1:N 관계 중 1;Foreign Key를 정의하지 않은 쪽이 사용)
posts = Post.prefetch_related(comments).filter(pk__gt = 3)
for post in posts:
    post.comments.text

```

- templates
```
1. template 에서 model.all(), model.count() 등 사용 시 아래와 같이 표현
{% model.all %} {% model.count %}

2. template 에서 로직 처리하는 것 보다 상위에서 처리 후 파라메터로 전달하는 게 좋아보임.
```

- Queryset, examples
ref. https://devvvyang.tistory.com/37

- Django model: ForeignKey, related_name(역참조), on_delete, RelatedManager, ...

- htmx
ref. https://htmx.org

- 예제 (pagination, search, ...)
ref. https://wikidocs.net/book/4223
ref. https://github.com/shop2world/ultrashop/blob/master/search/views.py
ref. https://www.shop2school.com/course/왕초보-파이썬-장고-python-django-쇼핑몰-따라-만들기/
