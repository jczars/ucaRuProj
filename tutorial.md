## Projeto ucaRu
### tutorial 1
https://wsvincent.com/django-allauth-tutorial/

## virtualenvs
python3 -m venv ~/.virtualenvs/ucaRuProj
source ~/.virtualenvs/ucaRuProj/bin/activate
pip install django
django-admin.py startproject ucaRuProj
cd ucaRuProj/
ls
./manage.py migrate
./manage.py runserver
pip install django-allauth

## # myproject/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('accounts/', include('allauth.urls')),
]./m	

## migrate
./manage.py migrate

https://github.com/settings/applications/new
https://django-allauth.readthedocs.io/en/latest/providers.html

## super user
./manage.py createsuperuser
jczars
jcdjangoss

## admin
http://127.0.0.1:8000/admin.
./manage.py runserver

### sites
127.0.0.1

### Social Applications
### google
https://console.developers.google.com/project

### create views.py
### myproject/views.py
from django.views.generic import TemplateView
class Home(TemplateView):
    template_name = 'home.html'
### myproject/settings.py
TEMPLATES = [
    ...
    'DIRS': [os.path.join(BASE_DIR, 'templates')],
    ...
]

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'ucaRu_bd',
        'USER': 'root',
        'PASSWORD': 'jc1122',
        'HOST': 'localhost',
        'PORT': '',
    }
}

### mySQL client
sudo apt-get install python-django
mysql -u root -p

mysql> create database ucaRu_bd;
mysql>exit

## templates
templates/home.html
<!-- templates/home.html -->
{% load socialaccount %}

<h1>Django Allauth Tutorial</h1>
{% if user.is_authenticated %}
<p>Welcome {{ user.username }} !!!</p>
{% else %}
<a href="{% provider_login_url 'google' %}">Sign Up</a>
{% endif %}

### myproject/urls.py
from django.contrib import admin
from django.urls import path, include

from . import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('accounts/', include('allauth.urls')),
    path('', views.Home.as_view(), name='home'),
]

./manage.py runserver
http://127.0.0.1:8000/admin/
logg de admin

127.0.0.1:8000

git init
git commint -m "first commit"

## criando app


# Criando o cardápio
class Cardapio(models.Model):
    pratoPrincipal = models.TextField(max_length=30)
    refeicao = models.TextField(max_length=30)
    salada = models.TextField(max_length=30)
    acompanhamento = models.TextField(max_length=30)
    sobremesa = models.TextField(max_length=30)
    observa = models.TextField(blank=True, null=True)
    dataCap = models.DateField(default=date.today)
    user = models.ForeignKey(User, on_delete=models.CASCADE)

./manage.py makemigrations
./manage.py migrate

# Register your models here.
admin.site.register(cardapioApp)

class Reserva(models.Model):
    resData = models.DateField(default=date.today)
    resHora = models.TimeField()
    idCap = models.ForeignKey(Cardapio, null=True, related_name='reservas')
    user = models.ForeignKey(User, default=1)


{% if user.username %}




