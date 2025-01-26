# MSDjango

Учебный проект "Новости Info to Go"
Урок 1
Создали проект itg
Создали репозиторий
Создали проект itg
Установили зависимости pip install django
Сохранили зависимости в файл requirements.txt командой pip freeze > requirements.txt
Развернуть проект на локальной машине через командную строку:

Склонировать репозиторий
Перейти в папку проекта
Создать виртуальное окружение python -m venv venv
Активировать виртуальное окружение source venv/bin/activate на Linux/MacOS или .\venv\Scripts\activate.bat на Windows
Установить зависимости pip install -r requirements.txt

Либо через PyCharm:
Склонировать репозиторий через File -> Project from Version Control
Установить зависимости через File -> Settings -> Project Interpreter или через pip install -r requirements.txt
Создание Django project
Создать проект django-admin startproject itg . Этой командой мы создадим проект с именем itg в текущей директории. Точка в конце команды означает, что проект будет создан в текущей директории, без создания дополнительной директории с именем проекта.

**commit: Урок 1: создаём django проект**



Запуск проекта python manage.py runserver Для запуска проекта, вам нужно использовать терминал, и находясь в директории проекта, на одном уровне с файлом manage.py, выполнить команду python manage.py runserver Для остановки сервера используйте комбинацию клавиш Ctrl+C

Команды терминала:

python manage.py runserver - запуск сервера
cd - смена директории
cd.. - переход на уровень выше
ls - просмотр содержимого директории
pwd - показать текущую директорию
commit: Урок 1: запускаем django сервер

Создание приложения python manage.py startapp news После создания приложения, вам нужно зарегистрировать его в файле settings.py в разделе INSTALLED_APPS

commit: Урок 1: cоздаём django_app news

Создали первое представление
from django.http import HttpResponse

def main(request):
    return HttpResponse("Hello, world!")  # вернет страничку с надписью "Hello, world!"
Чтобы представление заработало, его нужно зарегистрировать в файле urls.py конфигурации проекта.

Создали первый URL
from news import views

path('', views.main),
Теперь, если вы перейдете на главную страницу сайта, то увидите надпись "Hello, world!"

**commit: Урок 1: создаём первый маршрут и первое представление**


Урок 2
Создаем детальное представление новости по ее ID
Для этого нам нужно создать новый маршрут, с конвертом int, который будет принимать ID новости.

path('news/<int:news_id>/', views.news_detail),
А так же функцию, которая будет обрабатывать запрос и возвращать страницу с детальной информацией о новости.

def news_by_id(request, news_id):
    return HttpResponse(f"Новость с ID {news_id}")
include и собственный файл urls.py для приложения news
Создали еще одно представление get_all_news в файле views.py
Создали файл urls.py в директории приложения news
Зарегистрировали новый файл urls.py в файле urls.py конфигурации проекта с помощью функции include
Зарегистрировали маршруты без префикса news/ в файле urls.py приложения news

**commit: Урок 2: собственный urls.py в cards и функция include**
