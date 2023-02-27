# Blog Project

- [Blog Project](#blog-project)
  - [Installation](#installation)
    - [1. Need Packages](#1-need-packages)
    - [2. Install Django](#2-install-django)
  - [Create project](#create-project)
  - [To run the server](#to-run-the-server)
- [Applications and Routs](#applications-and-routs)
  - [Creating blog app](#creating-blog-app)
  - [Write first view](#write-first-view)
  - [First Migration](#first-migration)
    - [Create users app](#create-users-app)
    - [Crispy Forms Template](#crispy-forms-template)


Hi, we are going to learn how to build a full feature web application using django framework in python. Django is very popular framework that gives us a lots of functionality right of the box and makes very enjoyable to work with these web applications. First lets see what we are building in this series. And then get started learning how to actually put out together.

__Blog Features:__

- A blog style application where different users can write different posts. This can be a blog posts, twitter updates, Instagram post etc.
- We have an authentication system. Via __register__ new user can create a new account, if you have already account you can __login__ by username and password. Via __Forgot Password__ link that are allow to reset the password by getting an email. And __logout__ off course.
- User can view their __Profile__ page, update their profile information like - update username, update profile picture and that also resize in background to save picture in web server if that picture too large.
- On __Home__ page, you can view others people posts. Some post that you have written then you can modify or delete that post.
- Ability to Update/Delete that posts by double confirmation.
- Building something like this is great way to learn engine out of the framework because you gonna be exposed so many different things for example we learn how to work with databases & how to create an authentication system and (accepts user input from  __forms__ and send emails to reset password etc).
- Since this is __Django__ application we also have to ability to access admin page/Nice interface to be able to view all of the backend information and updated if you have the correct permissions.

## Installation

Okay lets get started with learning how to build this application using django then lets pull up terminal, so first of start by showing __packages__ that we need to get started out, we can do this on a __virtual environment__ or on a _default python environment_ but it's always a good idea to separate different projects into the own virtual environments.

### 1. Need Packages

- If you need to install python.
- How to work with virtual environment.
- or wondering how to set-up my text-editor. I have videos check out them.

With that said Let's get started -

### 2. Install Django

So, first lesson __install django__ so to do this we can simply do -

```shell
pip install django
```
- It install successfully django but, to be sure check the django version.

```shell
python -m django --version
```

- Use __python 3.7__ or higher version otherwise some of the features might not work in previous versions. There are some features that we use through this series such as __F String__ that are only available if you are running python 3.6 or higher.

Now lets create a new __project__ from scratch. You can create your project anywhere you would like in your machine. So, to create new a project we going to use some command that are available to us provided by django. One of these command is __`django-admin`__ so if you type, it should shows available __sub commands__.

```shell
# List of sub commands
django-admin
```

- We can see a lot of different sub commands listed here, we will see couple of this letter in project. But we are going to use one right now called __`startproject`__.
- So `startproject`: will create a new django project here, that has a complete structure with different files and everything we need to get started. Let's do that -

## Create project

```shell
django-admin startproject django_project
```

- Use underscore instead of dash.
- So we created a new project called __django-project__.
- If you look on your file explorer or desktop, now you have a directory called `django_project`.
- Let look at the project structure what that `startproject` command just created for us. For that cd the directory inside the project.

```shell
cd django_project
```

- Now open this project in a code editor.
- Now lets look at the project structure that startproject command created for us.
- Or you can also view in terminal, Let me show structure in command line interface.

```shell
tree
```

![TreeStructure](images/project_structure-tree-command.png)

```shell
.
|--- django_project
|     |-- __init__.py
|     |-- asgi.py
|     |-- settings.py
|     |-- urls.py
|     |-- wsgi.py
|
|--- manage.py
```

- Now we can see here in structure, that on base level we have a `manage.py` and a `django_project` directory.
- __`manage.py`__: is a file that allows us to run main line command & we don't want making any changes here.
- __`django_project`__: We also have a directory called `django_project` which is also the name that used in our project itself. Within this directory we have 5 different files.

1. __`__init__.py`__: It just an empty file. That just tells python this is just python package.
2. __`settings.py`__: Next we have `settings.py` as it tells probably by name, this where we can change different settings and configurations so we will be using this through out series or development.

We can see that most of this files have good documentation and links provided where we can learn more information. Now if you glance through here in `settings.py`.
   - __SECRETE_KEY__: That just add lots security enhancement to django. We also have __DEBUG__, __INSTALLED_APPS__, __DATABASE__ settings and all kinds of different useful settings that we will talk about more in future.

3. __`urls.py`__: This is where we will set up the mapping from certain urls to where we send the user.
4. __`wsgi.py`__: is how our python web application and web server will communicate.

Now let's open up default website in our browser. To open up website in browser, we have to run a command -

## To run the server

Stay with same directory where `manage.py` file is then run -

```py
python manage.py runserver
```

- You might have warning we will fix next time that says you have 15 unapplied migrations and that suggest to run command, let's not do that.

Now open in browser [http://127.0.0.1:8000/](http://127.0.0.1:8000/). Another name is [http://localhost:8000/](http://localhost:8000/).
- localhost = 127.0.0.1

This is the default website that django has created for us and in this series we will modify this.

`127.0.0.1` was the IP address of the local machine. And also there are alias for that IP address called as `localhost`.

- To stop the server by `ctr` + `c`.

In, __DEBUG__ mode it should automatically reload any changes that made to our code.

# Applications and Routs

In this, we will be adding a blog application to site and also setting up some url routs so that we can start direct people to that he would like to see. Let's get started.

## Creating blog app

First lets create a __blog app__ for our site. The thinking behind the django here, is that you have the website project which we already created within that website we can have multiple apps for example we can have a blog section of our website that will be an app. And we can also have __store app__ section of the website.

- A single project can contain multiple apps like blog app, store app.

We will see in letter, that good thing for separating out different parts of the project. And another thing we can add single apps to multiple projects.

__Creating blog app:__

Stay on project directory in the same directory where `manage.py` file.

```py
python manage.py startapp blog
```

- Lets see the layout of the file structure -

```
--- 8blog
|   |--- __init__.py
|   |--- admin.py
|   |--- apps.py
|   |--- migrations
|   |       |--- __init__.py
|   |--- models.py
|   |--- tests.py
|   |--- views.py
|--- db.sqlite3
|--- django_project
|       |--- __init__.py
|       |--- settings.py
|       |--- urls.py
|       |--- wsgi.py
|--- manage.py
```

## Write first view

You can see we already have imported __render__ we use that letter. But for now we also going to import `HttpResponse` from `django.http`.

__Write in `blog/views.py`:__

```py
from django.shortcuts import render
from django.http import HttpResponse

def home(request):
    return HttpResponse('<h1>Blog Home</h1>')
```


- map the url in `/blog` create a new file `urls.py` and write -

```py
from django.urls import path

from . import views

urlpatterns = [
    # creating path for blog home page
    path('', views.home, name='blog-home'),
]
```


## First Migration

- First create super user.

```py
python manage.py createsuperuser
```

- Second you change `models.py` in app.
- then commands to migrate

```py
python manage.py makemigrations

python manage.py sqlmigrate blog 0001

python manage.py migrate

python manage.py shell
```

Write in migrate shell ->

```py
from blog.models import Post
from django.contrib.auth.models import User

# See all users
User.objects.all()

# First user
User.objects.first()

# Last User
User.objects.last()

# Filter result of user
User.objects.filter(username='Irfan')

# First of filter result
User.objects.filter(username='Irfan').first()

# Store user in a variable 
user = User.objects.filter(username='Irfan').first()

# To see id of user
user.id

# Primary Key of user which is same as id
user.pk

# get user by id
user = User.objects.get(id=1)

'''
Lets create a new post which author is this user
'''

# Check all posts
Post.objects.all()

# Create post
post_1 = Post(title='Blog 1', content='First Post Content!', author=user)
# or
post_2 = Post(title='Blog 2', content='Second Post Content!', author_id=user.id)

# after creation of post you have to save
post_1.save()
Post.objects.all()

# To exit shell
exit()

# Post save into variable
post = Post.objects.first()

# Now you can access all fields
post.content
post.date_posted
post.author
post.author.email               # grab email of author user


# general command
.modelname_set

# Get all post written by a user
user.post_set
user.post_set.all()

# Create post using post_set
user.post_set.create(title='Blog 3', content='Third Post Content!')
```

### Create users app

```py
python manage.py startapp users
```


### Crispy Forms Template

```py
pip install django-crispy-forms
```
