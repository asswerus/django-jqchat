#############
Django-jqchat
#############

Welcome
=======

This is a django app that implements a very basic chat client.


Get started
===========

* Clone locally: **git clone https://github.com/asswerus/django-jqchat.git**


In order to use django-jqchat, you have to set up the application in which the chat will be hosted, 
like in the following example.

**Installing dependencies**

* pip install django
* pip install pytz

**Creating the project**

* django-admin.py startproject demo

**Configuring the chat**

* Copy the **jqchat** folder (you find it into you local clone folder) to the **demo** folder (the one containing
the settings.py file)
* Add **jqchat** to the **INSTALLED_APPS** property in your **settings.py** configuration file

```python
INSTALLED_APPS = (
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'jqchat',
)
```


* Execute **python manage.py syncdb**
* Open the file **demo/urls.py** and add the following:

```python
import jqchat
...
url(r'^chat/', include('jqchat.urls')),
```

* Through the django admin interface (usually http://localhost:8000/admin after executing manage.py runserver) 
create a **Room**

**Creating the base template**

* In the **demo** folder (where you settings.py is) create a folder named **html**
* In the folder **html** create a file named **base.html** and fill it with the following:

```html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
      <title>Demo for Django-jqchat</title>
      <script src="//code.jquery.com/jquery-1.11.0.min.js"></script>
      {% block extra_head %}{% endblock %}
   </head>
   <body>
   	{% block body %}{% endblock %}
   </body>
</html>
```

* Open your **setting.py** and add the following

```pyton
TEMPLATE_DIRS = (os.path.join(BASE_DIR, 'demo'),)
```

* Lauch the apllication by executing **python manage.py runserver**
* Access your Room at http://localhost:8000/chat/room/1
