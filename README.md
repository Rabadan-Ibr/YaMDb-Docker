# Yamdb
REST API для Yatube. Документация: http://127.0.0.1/redoc/.
##### Возможности:
- Создание пользователя.
- Получение токена аутентификации пользователя.
- Просмотр списка публикаций и информации о конкретной публикации.
- Размещение и изменение публикаций с возможностью указания группы.
- Просмотр всех комментариев к конкретной публикации и отдельного комментария.
- Размещение и редактирование комментариев.
- Просмотр списка существующих групп и информации об конкретной группе.
- Возможность подписаться на конкретного автора и увидеть список подписок.


### Технологии:
- Python
- Django
- REST API
- Docker
- nginx

##### Шаблон наполнения env-файла:
Разместить в "infra/"
- DB_ENGINE= указываем тип БД
- DB_NAME= имя базы данных
- POSTGRES_USER= логин для подключения к базе данных
- POSTGRES_PASSWORD= пароль для подключения к БД
- DB_HOST= название сервиса (контейнера)
- DB_PORT= порт для подключения к БД 

#### Описание команд для запуска приложения в контейнерах:
Перейти в директорию "infra/" и выполнить оттуда команду: 
``` docker-compose up ```.\
По окончании создания и запуска контейнеров выполнить миграции: 
```docker-compose exec web python manage.py migrate```.\
Создать суперпользователя: 
```docker-compose exec web python manage.py createsuperuser```.\
Собрать статику: 
```docker-compose exec web python manage.py collectstatic --no-input```.

#### Описание команды для заполнения базы данными.
Выполнить из директории "infra/"
```docker-compose cp fixtures.json web:/app```. 

```docker-compose exec web python manage.py loaddata fixtures.json```

### Авторы проекта:
Мария Постолова — Отзывы, Комментарии, эндпоинты, разрешения.
Рабадан Ибрагимов — Категории, Жанры, Произведения, импорт из CSV в БД, Рейтинг Произведений, эндпоинты, разрешения, Docker.
Александр Колесов — Регистрация и аутентификация пользователей, Роли, подтверждение через Email, выдача токена, эндпоинты, разрешения.
