# django-cheatsheet
Some Django Cheat Sheet

```
django-admin startproject mysite

python manage.py runserver

python manage.py runserver 8080

py manage.py runserver 80

python manage.py startapp frontend

py manage.py help

py manage.py makemigrations

py manage.py migrate

python manage.py createsuperuser

# urls.py
from django.contrib import admin
from django.urls import include, path
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('frontend.urls')),
]  + static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)

# settings.py
INSTALLED_APPS = [
    'frontend.apps.FrontendConfig',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]

# frontend/urls.py

from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
    path('secret/', views.secret, name='secret'),
    path('<int:id>/', views.bypass, name='detail'),
    # ex: /5/results/
    #path('<int:question_id>/results/', views.results, name='results'),
    # ex: /polls/5/vote/
    #path('<int:question_id>/vote/', views.vote, name='vote'),
]

# frontend/views.py
from django.shortcuts import get_object_or_404, render
from django.http import HttpResponse
from django.template import loader

from .models import Category
from .models import Image
from .models import Video
from .models import Ig


import requests
import json
from datetime import datetime
import re



def login_method( request ):

    if request.method == 'POST':
        form = request.POST
        if form.get('username'):
            username = form.get('username')

def index( request ):

    data = {}

    return render( request, 'frontend/index.html', data )
	
	
# html tags

{% include "frontend/nav.html" %}
{% load static %}
{{ dataindex }}
```
