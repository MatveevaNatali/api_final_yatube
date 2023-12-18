api_final_yatube
Автор - [Матвеева Наталия](https://github.com/MatveevaNatali)

## Описание:

Финальная часть учебного проекта социальной сети, в которой есть возможность публиковать записи, комментировать их и подписываться/отписываться от авторов.

## Технологии:
Python, Django, DRF, JWT + djoser

## Как запустить проект:

Клонируй репозиторий и перейди в него в командной строке:

git clone https://github.com/sergeypatrakov/api_final_yatube

 cd api_final_yatube

Cоздай и активируй виртуальное окружение:

python3 -m venv venv

source venv/scripts/activate

python3 -m pip install --upgrade pip


pip install -r requirements.txt

Выполни миграции:

python3 manage.py migrate

Запусти проект:

python3 manage.py runserver

## Пример работы API для неавторизованного пользователя:
Неавторизованные пользователи могут только читать контент, они не могут создавать или менять что-то. Для неавторизованных пользователей недоступен эндпоинт follow.

GET http://127.0.0.1:8000/api/v1/posts/ Получение всех записей.\
Пример ответа:
```
{
"text": "string",
"image": "string",
"group": 0
}
```
GET http://127.0.0.1:8000/api/v1/posts/?limit=2&offset=4 Звпрос с параметрами limit  и offset \
Такой GET-запрос вернёт два объекта, с пятого по шестой (или меньше, если в результате запроса менее 6 объектов).\
Пример ответа:
```
{
"count": 123,
"next": "http://127.0.0.1:8000/api/v1/posts/?limit=2&offset=7",
"previous": "http://127.0.0.1:8000/api/v1/posts/?limit=2&offset=2",
"results": [{}]
}
```
GET http://127.0.0.1:8000/api/v1/posts/{id}/ Получение публикации по id. \
Пример ответа:
```
{
"text": "string",
"image": "string",
"group": 0
}

## Пример работы API авторизованного пользователя:
POST http://127.0.0.1:8000/api/v1/posts/ Создание новой записи, поле text - обязательное.
Пример запроса:
```
{
"text": "string, required field",
"image": "string", 
"group": integer 
}
```
Пример ответа:
```
{
"id": 0,
"author": "string",
"text": "string",
"pub_date": "2019-08-24T14:15:22Z",
"image": "string",
"group": 0
}
```
