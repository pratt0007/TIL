# Django: 
- Django is a high-level Python web framework which is based on MVT architecture.

## MVT (Model View Template):
- The MVT is an design pattern that separates an application into three main logical componentsL
  - **Model:**
    - The Model responsible to handle database. It is a data access layer which handles the data.
    - Written in Python (Need knowledge about Databases)
  - **View:**
    - The user can send request by interacting with template, the view handles these requests and sends to Model then get appropriate response from the Model, sends response to template. It works as a mediator between Template and Model.
    - It may also have required logics (Python)
  - **Template:**
    - It represents how data should be presented to the application user. User can read or write the data from template. Basically it is responsible for showing end user content, we can say it is user interface.
    - It may consists of HTML, CSS, JS mixed with Django Template Language.

<img width="1338" alt="MVT" src="https://github.com/IshaanAdarsh/TIL/assets/100434702/2795db0a-6c70-48b7-bdf5-e1023228f439">

## Django Project Directory Structure:
```
project_name/          # Project root directory / Outer Project Folder
|-- project_name/      # The main Django application directory / Inner Project Folder
|   |-- __init__.py
|   |-- asgi.py        # ASGI configuration (for Channels and asynchronous support)
|   |-- settings.py    # Django settings file
|   |-- urls.py        # URL configuration for the project
|   |-- wsgi.py        # WSGI configuration for deployment
|-- manage.py          # Django's command-line utility for administrative tasks
```
### `myproject/`: 
This is the root directory of your Django project. You can give it any name you prefer.

### `manage.py`: 
A command-line utility that allows you to interact with various Django commands, such as running the development server, creating database tables, etc. Its sets `DJANGO_SETTINGS_MODULE` environment variable so it points to `settings.py`.If you are working on a single Django Project it is preferred to use `manage.py` rather than `django-admin`.

### `myproject/`: 
This is the main Python package directory that contains all the settings and configurations for your project.

### `__init__.py`: 
An empty file that marks the `myproject/` directory as a Python package.

### `settings.py`: 
The settings file where you define all the configurations for your Django project, such as database settings, installed apps, middleware, etc. [Detailed Information](https://github.com/IshaanAdarsh/TIL/blob/main/Django/Extra%20files/settings_py.md)

### `urls.py`: 
The URL configuration file where you define the URL patterns and map them to view functions.

### `wsgi.py`: 
The WSGI (Web Server Gateway Interface) entry-point file used for running Django applications with traditional web servers. Work in this file when you need to interact with the web server

<img width="1385" alt="Wsgi" src="https://github.com/IshaanAdarsh/TIL/assets/100434702/fb75ccf4-5d01-4685-81da-ff7e1361d788">

- Django uses the `DJANGO_SETTINGS_MODULE` environment variable to locate the settings module for your application. It should contain the dotted path to the settings module. If not set, the default `wsgi.py` sets it to `mysite.settings`, where `mysite` is the project name. This allows `runserver` to discover the default settings file automatically. You can use different values for development and production based on your organization of settings.

### `asgi.py`: 
The ASGI (Asynchronous Server Gateway Interface) entry-point file used for running Django applications with asynchronous servers. The successor of `wsgi.py` as it provides a standard for both synchronous and asynchronous apps

<img width="711" alt="asgi" src="https://github.com/IshaanAdarsh/TIL/assets/100434702/6d34848a-c1ce-4d60-9f09-975293487f46">

When we run the command `python3 manage.py runserver`, some new files are created.
```
project_name/          
|-- project_name/
|   |-- __pycache__/
        (Python cache files)
|   |-- __init__.py
|   |-- asgi.py        
|   |-- settings.py    
|   |-- urls.py        
|   |-- wsgi.py        
|-- db.sqlite3
|-- manage.py
```
The new files are:
- `__pycache__/`: A directory that contains Python cache files for improved import performance.
- `db.sqlite3`: The SQLite database file where the data for your application is stored.

## Django Server Working:
Django provides built-in server which we can use to run our project. 
- `runserver` : This command is used to run built-in server of Django.

### Steps:-
- Go to Project Folder
- Then run command `python manage.py runserver`
  - Server Started. Visit `http://127.0.0.1:8000` or `http://localhost:8000`
- You can specify Port number in the end to run the project in a specific port: `python manage.py runserver 5555`
  - Visit http://127.0.0.1:5555 or http://localhost:5555

## Django Application:
### Creating a Django Application:
- A Django project contains one or more applications which means we create applications inside ProjectFolder.
Syntax:- `python manage.py startapp appname`
**Steps:**
- Go to Project Folder
- Run the syntax, if you want to create multiple applications run the syntax multiple times with different appnames.
```bash
python manage.py startapp course
```

### Installing a Django Application:
- We install application in our project using `settings.py` file. This is compulsory otherwise Application won't be recognized by Django.
**Steps:**
- Open `settings.py` file
- Add the names of the applications to the INSTALLED_APPS field and save `settings.py`
```python
# Install the applications course, fees, and result
INSTALLED APPS = [
'django.contrib.admin',
'course',
'fees',
'result',
]
```

### Application Directory Structure:
```
myapp/              # Your application's main directory
    __init__.py     # An empty file that makes this directory a Python package

    admin.py        # Configuration for the Django admin interface
    apps.py         # Application configuration
    models.py       # Database models
    tests.py        # Test cases for the application
    views.py        # Views that handle HTTP requests and render templates

    migrations/     # Directory for database migrations
        __init__.py # An empty file that makes this directory a Python package
```
- `__init__.py`: This file is required to treat the `myapp` directory as a Python package.

- `admin.py`: This file is used to register sql tables so we could perform CRUD operations from Admin Application. Admin Application is provided by Django to perform CRUD operation.

- `apps.py`: This is the configuration file for your application. It allows you to customize certain aspects of your app, such as the app's name and label.

- `models.py`: This file is used to create our own model class later these classes will be converted into a database table by Django for our application.

- `tests.py`: This file is for writing test cases to test the functionality of your application.

- `views.py`: This is where you define the views (functions or classes) that handle HTTP requests and return HTTP responses. Views are responsible for processing data and rendering templates. We write all the buisness related logic in this file/

- `migrations/`: This directory is automatically created by Django and is used to store database migration files. Migrations help you manage changes to your database schema over time. It also contains all files that are created after running `makemigration` command (keeps database-related files).

<hr>

# View:
## Function Based View:
- A function-based view in Django is a Python function that handles web requests and generates web responses, such as HTML pages, redirects, or error messages.
- We use `views.py` file of the application to write functions which may contain the business logic of the application, later it is required to define url name for this function in the `urls.py` file of the project.
  - It takes an `HttpRequest` object as a parameter and returns an `HttpResponse` object to provide the response content.
```python
def function_name (request):                          # request -> httpRequest Object
  return HttpResponse('html/variable/text')           # HttpResponse -> Class
                                                      # html/variable/text -> httpResponse Object
```

## URL Dispatcher:
- To design URLs for app, you create a Python module informally named urls.py. This module is pure Python code and is a mapping between URL path expressions to view functions.

![URL-Dispatcher](https://github.com/IshaanAdarsh/TIL/assets/100434702/af7bcaa9-5450-4375-931e-fea234a800c0)

### path ( )
`path(route, view, kwargs=None, name=None)` : It returns an element for inclusion in urlpatterns.
- The route argument must be a string or gettext_lazy() containing a URL pattern with angle brackets (<>) to capture parts of the URL as keyword arguments for the view.
  - Angle brackets can include converter specifications like <int:id> to limit characters matched and change the variable type passed to the view (e.g., converting to an integer).
- The view argument is a view function or the result of as view for class-based views.
It can also be an django.urls.include.
- The kwargs argument allows you to pass additional arguments to the view function or method. It should be a dictionary.
- name is used to perform URL reversing.

```python
# urls.pr Sample Syntax
urlpatterns = [
  path(route, view, kwargs=None, name=None)
]

# urls.py Example
urlpatterns = [
  path(learndj/', views.learn_Django, {'check': 'OK'), name= 'learn django'),
]
```

### Steps to use View Funtion and URL Dispatcher at Project level:  
#### 1) Edit the Views.py:
- Where `HttpResponse` is class which is in `django.http` module so we have to import it before using `HttpResponse`.
```python
from django.http import HttpResponse

# Inside views.py different ways to use a funtion
def learn_django(request):
  return HttpResponse('Hello Django')                  # Simple Return Statement

def learn_python(request):
  return HttoResponse('<hI>Hello Puthon</hI>')         # HTML Return Statement

def learn_var(request):
  a ="<h1>Hello Variable</hi>'                         # HTML using variable
  return HttpResponse(a)

def learn_math(request):
  a = 10 + 10                                          # Maths using variable
  return HttpResponse(a)

def index(request):
  return HttpResponse('Home Page')                   # To remove the 404 error, need to specify the homepage
```

#### 2) Edit the Urls.py:
- Add the urls for the view funtion.
```python
form course import views                         # Need to import the views form the application course

# Update the urls to point to the new changes
urlpatterns = [
  path('admin/', admin site.urls),
  path(learndj/', views.learn_django),
  path('',views.index),                          # '' -> points to the no url so the default http://127.0.0.1:8000
  path(altlearndj/, views.learn_Django),         # We can define multiple url for one view function.
]
```
- Visit the URL : http://127.0.0.1:8000          -> Homepage
- Visit the URL : http://127.0.0.1:8000/learndj/ -> Hello Django

### Multiple Application inside Project and their Function Based Views:
- Add funtions to the `views.py` of the individual applications and then add thier details in the `urls.py` of the main folder.

```python
# Incorrect urls.py
# As they have the same name (views), we have to sepcify which views.py we are talking about. Is it the course.view or fees.views
from course import views
from fees import views
  urlpatterns = [
    path(learndj/', views.learn_django),
    path(feesdj/', views.fees _django),
]

# Correct urls.py
# Method 1: Aliasing
from course import views as cv
from fees import views as fv
  urlpatterns = [
    path(learndj/', cv.learn_django),
    path(feesdj/', fv.fees _django),
]

# Method 2: Individual funtions (More reductive, not preferred)
urls.py
from course.views import learn_django
from fees.views import fees _django
  urlpatterns = [
    path (learndj/', learn_django),
    path (feesdj/', fees_django),
]
```
- But our each application should be independent or less depend on project so we could use our applications in different projects easily without worrying about `urls.py` available in Project Folder. We need to use url pattern inside Application to Reduce the dependency of Application, Enhance Application performance and Reusability of application becomes easy.

### View Funtion and URL Pattern inside Application:  
#### include():
- The `include()` function in Python includes another URLconf module using its import path. It can take optional arguments for specifying namespaces and accepts an iterable or a 2-tuple containing URL patterns and application namespaces. This allows for flexible and modular URL configuration.
- `path(route, view, kwargs=None, name=None)`
- The view argument is a view function or the result of as view for class-based views. It can also be an django.urls.include.

```python
# Syntax
Syntax:-
include(module, namespace=None)
include(pattern list)
include((pattern_ list, app_ namespace), namespace=None)

# Example:
# Method 1: straight linking
from django.urls import include, path
  urlpatterns = [
    path('cor/', include('course.urls')),
]

# Method 2: Using Lists
urlpatterns = [
  path('cor/', include([
    path('learndj/', views.learn _django),
    path('learnpy/', views.learn_python)
  ])),
]

# Same as above code:
otherpatterns = [
  path('learndj/', views.learn django),
  path('learnpy/', views.learn python),
]
urlpatterns = [
path('cor/', include(otherpatterns),
]
```

### Steps: 
#### Write URL Pattern inside Application
- Create an `urls.py` file inside each application (in case multiple application).
- Write all url pattern related to application, in `urls.py` file available inside application.
- Include Application's `urls.py` file inside Project's `urls.py` file.

```python
# views.py in Application Folder
from django.http import HttpResponse
def learn_django(request):
  return HllpResponse('Hello Django')
def learn_python(request):
  return HttpResponse(*<hI>Hello Python</hI>')

# urls.py in Application Folder
from course import views
  urlpatterns = [
    path('learndj/', views.learn django),
    path(learnpy/', views.learn_python),
]

# urls.py in Project Folder
from django.urls import path, include
urlpatterns = [
  path(cor/, include('course.urls')),          # course -> Package Name, urls -> Module Name
]
```
Links to viist the applications:
- http://127.0.0.1:8000/cor/learndj 
- http://127.0.0.1:8000/cor/learnpy

<hr>

# Template:
- A template is a text file. It can generate any text-based format (HTML, XML, CSS, etc). It contains variables, which get replaced with values when the template is evaluated, and tags, which control the logic of the template. Template is used by view function to represent the data to user.

### Creating Templates:
- We create `templates` folder inside Project Folder,this folder will contain all HTML files.
- Add templates in `settings.py`
  - Create a variable `TEMPLATES_DIR` and add it to the `TEMPLATES` List

```python
# settings.py
TEMPLATES_DIR = os.path.join(BASE_DIR,'templates')

TEMPLATES = [
  {
    'DIRS': [TEMPLATES _ DIR],
    # Directories where the engine should look for template source files, in search order.
  }
]
```

### Writing Template Files:
- When we create Template file for application we separate business logic and presentation from the application views.py file.
- We write business logic in views py file and presentation code in template file.

### Rendering Templates Files:
- Still `views.py` will be responsible to process the template files for this we will use `render()` function in `views.py` file.
### render ()
- `render() Function`: It combines a given template with a given context dictionary and returns an HttpResponse object with that rendered text.

`render(request, template_name, context=dict _ name, content_type=MIME_type, status=None, using=None)`

- **request**: The request object used to generate this response. */
- **template_name**: The full name of a template to use or sequence of template names. If a sequence is given, the first template that exists will be used. */
- **context**: A dictionary of values to add to the template context. By default, this is an empty dictionary. If a value in the dictionary is callable, the view will call it just before rendering the template.
- **content_type**: The MIME type to use for the resulting document. Defaults to 'text/html'.
- **status**: The status code for the response. Defaults to 200.
- **using**: The NAME of a template engine to use for loading the template.

> */ -> Manatory Fields to include for the reder function to execute

```python
# views.py
from django.shortcuts import render
def function name(request):
  # Dynamic Data can be written, if else, any python code logic
    return render(request, template _ name, context=dict name,
    content_type=MIME_type, status=None, using=None)

# Example:
def learn django(request):
  return render(request, 'courseone.html')

# Example:
def learn django(request):
  render(request,'courseone.html',context=cname,content_type='application/xhtml+xml')
```

### Creating and Rendering Templates File For each Application Separately:
- We can create separate folder inside templates folder for applications then each application will contain only those HTML file which are related to them. This will enhance readability and separate HTML files according to applications.

![Template_naming](https://github.com/IshaanAdarsh/TIL/assets/100434702/865f261c-0f8d-4bda-9433-757517c996f9)

- Follow the same steps for the writing and creating of template files (just make seperate files for more clarity)
- Just in the Rendering Process of the templates edit the template name to reflect the template path

```python
# views.py
def learn django(request):
  return render(request,'course/courseone.html')          # Reflects the chnae form courseone.html to new location
```

## Dynamic Template Files using DTL:
- For more detailed information about [DLT](https://github.com/IshaanAdarsh/TIL/blob/main/Django/Detailed%20Information/DLT.md)
- Use variables in the HTML files using Django Template Language
```python
# views.py
from django.shortcuts import render
def function name(request):
  # Dynamic Data, if else, any python code logic
    return render(request, template _name, context=dict_name, content_type=MIME_type, status=None, using=None)

# views.py
from django.shortcuts import render
def learn_django(request):
  coursename = {'cname': 'Django'}
  return render(request, 'course/courseone.html', context coursename)
  # OR
  return render(request, 'course/courseone. html', coursename)
  # OR
  return render(request,'course/courseone.html',{'cname': 'Django'})

# Example:
# views.py
from django.shortcuts import render
def learn django(request):
    cname = 'Django'
    duration = '4 Months
    seats = 10
    django_details = ('nm' :cname, 'du': duration, 'st' :seats}
    return render(request, 'course/courseone.html', django_details)
```
- Write the HTML using the variables
```html
// courseone.html
<html>
  <body>
    <h2> Course Name: {{nm}} Duration: {{du}} and Total Seats: {{st}}</h2>
  </body>
</html>
```

## Templates inside Application:
- Create a templates folder inside each application
  - Check 'APP DIRS': True in settings.py
```python
# settings.py
INSTALLED APP = [
    'course',
    'fees'
]

TEMPLATES = [
  {
    'DIRS': [],
    'APP_DIRS':True,
  }
]
```

## Templates inside and outside the Application:
- Just add a `DIRS` value to the variable 
```python
# settings.py
TEMPLATES_DIR; = os.path.join(BASE_DIR,'templates')
INSTALLED APP = [
    'course',
    'fees'
]

TEMPLATES = [
  {
    'DIRS': [TEMPLATES_DIR],
    'APP_DIRS':True,
  }
]
```

## Static Files inside Project:
- CSS files, Javascript Files, image files, video files etc are considered as static files in Django. 
- Django provides `django.contrib.staticfiles` to help you manage them. `django.contrib.staticfiles` collects static files from each of your applications (and any other places you specify) into a single location that can easily be served in production.

### Steps:
- We create static folder inside Root Project Folder then inside static folder we create required folders which will contain all static files respectively like css folder will contain all ess files, image folder will contain all images and so on.
```python
# Directory Structure:
geekyshows
  static
    CSS
      style.css
      custom.css
    images
      love.jpg
      pic1.jpg
```

#### Add Static in settings.py
```python
# settings.py
TEMPLATES_DIR = os.path.join(BASE_DIR,'templates')
STATIC_DIR = os.path.join(BASE _DIR,'static')
INSTALLED APPS= [
      'course'
]
TEMPLATES = [
  {
    'DIRS': [TEMPLATES_DIR]
  }
]
STATIC URI = "static/
STATICFILES DIRS = [STATIC DIR]
```

### Use Static Files in Template Files
- First Load Static Files
- Reference Static Files
```html
// templates/course
// courseone.html
<!DOCTYPE html>
{% load static %}      // Loading Static Files (Load Tag)
<html>
  <link href='{%static "css/stvle.css"%}'>      // Referece Static Files
    <body>
      <h1>Fees {{fe}}</h1>
      <img src='{%static "images/love.jpg"%}>   // Referece Static Files
    </body>
</html>
```

#### `load` Template Tag:
- It loads a custom template tag set.
- Sytntax: `{% load module _name %} `
```html
Template would load all the tags and filters registered in emotags and mytags located in package geek.
Example:- {% load emotags %}                    // Loaded total Module emotags
Example:- 4% load geek.mytags %}                // Load the package instide module
Example:- {% load emotags geek.mytags %}        // Load Both

You can also selectively load individual filters or tags from a library or module, using the from argument.
Example - {% load cry lol from emotags %}       // The template tags/filters named cry and lol will be loaded from emotags.
```

#### `static` Template Tag:
- This tag is used to link to static files that are saved in STATIC_ROOT. If the django.contrib.staticfiles app is installed, the tag will serve files using url method of the storage specified by `STATICFILES STORAGE`.
```html
// Syntax:-
1) {% load static %}
2) {% static filename %}
3) {% static path/filename %}
4) {% static path/filename as variable %}
Example:-
1) <link rel="stylesheet" href="{% static 'style.css' %}" >

2) <link rel="stylesheet" href="{% static 'css/style.css' %}" >

3) <img src="{% static 'images/love.jpg' %}">

4) {% static "images/love.jpg" as mylove %}
<img src="{{ mylove }}">
```
#### `get_static_prefix` Template Tag:
- `{% get _static_prefix %}`: We should prefer the static template tag, but if you need more control over exactly where and how STATIC URL is injected into the template, you can use the get static prefix template tag.
```html
Example:-
{% load static %}
<img sre="{% get static _prefix %} images/love.jpg">

There's also a second form you can use to avoid extra processing if you need the value multiple times.
{% load static %}
{% get static prefix as STATIC PREFIX %}
<img sre=" {{STATIC_PREFIX}} images/love.jpg">
<img src="{{STATIC _PREFIX}} images/pic1.jpg">
```

### STATIC_URL:
- This is the URL to use when referring to a static file located in `STATIC_ROOT`. It must end in a slash if set to a non-empty value.
```python
Example:- "static/"
Example:- "http://static.example.com/"
```

### STATIC_ROOT: 
- This is absolute path to the directory where `collectstatic` command will collect static files for deployment. It is by default None.
```python
Example:- "/var/www/example.com/static/"
Example:- os.path.join(BASE_DIR, 'static/')
```

### STATICFILES_DIRS: 
- This setting defines the additional locations the staticfiles app will traverse if the FileSystemFinder finder is enabled, e.g. if you use the collectstatic or findstatic management command or use the static file serving view. It is by default an empty list.
```python
STATICFILES_DIRS = [
"/home/special.geek.com/geek/static"
"home/geek.com/geek/static"
"opt/webfiles/common",
]
```

### STATICFILES_STORAGE:
- The file storage engine to use when collecting static files with the collectstatic management command.
```python
Default: 'django.contrib.staticfiles.storage.StaticFilesStorage'
```
#### Steps:
- Create Django Project: django-admin startproject geekyshows
- Create Django ApplicationI: python manage.py startapp course
- Create Django Application2: python manage.py starlapp fees
- Add/Install Applications to Django Project (course and fees to geekyshows) using settings.py INSTALLED APPS
- Create templates folder inside each application and inside Root Project Folder
- Check 'APP DIRS': True in settings.py
- Add templates directory which is inside Root Project Folder, in settings.py
- Create folder inside app/templates directory for template files
- Create template files inside app/templates/folder
- Create template files inside templates folder which is inside Root Project Folder
- Create static folder inside Root Proiect Folder
- Create css, js, images, video etc folder inside static folder
- Create static files inside css, js, images, video etc folder.
- Write View Function inside views.py file
- Define url for view function of application using urls.py file
- Write Template files code
- Write Static file code

## Static Files inside Application:
- We create static folder inside Application Folder then inside static folder we create required folders which will contain all static files respectively like css folder will contain all ess files, image folder will contain all images and so on.

### Changes to `setting.py`:
```python
# settings.py
TEMPLATES_DIR; = os.path.join(BASE_DIR, 'templates')
STATIC_DIR = os.path.join(BASE_DIR,'static')

INSTALLED APPS = [
  'course`
]

TEMPLATES = [
  {
    'DIRS': [TEMPLATES_DIR]
  }
]

STATIC_URL =  '/static/'
STATICFILES_DIRS = [STATIC_DIR]
```

### Use Static Files in Template Files:
- First Load Static Files
- Reference Static Files
```html
// templates/course
// courseone.html
<!DOCTYPE html>
{%load static %}    // Loading Static Files
<HTML>
 <link href=' {%static "course/css/style.css"}>
  <body>
    <h1>Fees {{fe}} </h1>
    <img src=* (%static "course/images/picl.jpg"}>
  </body>
</html>
```

## Static Folder and Files inside Project & Application:
### Add Static in `settings.py`:
```python
# settings.py
TEMPLATES _DIR; = os.path.join(BASE _DIR,'templates')
STATIC_DIR = os.path.join(BASE _DIR,'static')

INSTALLED_APPS = [
    'course'
]

TEMPLATES = [
  {
    'DIRS': [TEMPLATES_DIR]
  }
]

STATIC_URL = '/static/'
STATICFILES_DIRS = [STATIC_DIR]
```

### Use Static Files in Template Files:
- First Load Static Files
- Reference Static Files
```html
<!DOCTYPE html>
{%load static %}        // Loading Static Files
<html>
  <link href= '{%static "css/some.css"}'>
  <body>
    <h1>Fees {{fe}} </h1>
    <img src= '{%static "course/images/picl.jpg"}'>
  </body>
</html>
```

# Template Inheritance:
- Template inheritance allows you to build a base "skeleton" template that contains all the common elements of your site and defines blocks that child templates can override.
- The `extends` tag is used to inherit template. `extend`s tag tells the template engine that this template "extends" another template.When the template system evaluates this template, first it locates the parent let's assume. "base.html".At that point, the template engine will notice the block tags in base. html and replace those blocks with the contents of the child template.

## `extends` tag:
- `{% extends %}`: The extends tag is used to inherit template. It tells the template engine that this template "extends" another template. It has no end tag.
```python
# Syntax:-
{%extends 'parent_template_name'%}
{%extends variable%}

# Example:-
{% extends "./basel.html" %}
{% extends "../base2.html" %}
{% extends "./my/base3.html" %}
{% extends somthing %}
```

## `block` Tag
- `{% block %}`: The block tag is used to for overriding specific parts of a template.
```python
# Syntax:-
{% block blockname %} ..... {% endblock %}
{% block blockname %} ..... {% endblock blockname %}

# Example:-
{% block title %} .... {% endblock %}
{% block content %} ..... {% endblock content %}
```

### Rules
- If we use {% extends %} in a template, it must be the first template tag in that template. Template inheritance won't work, otherwise.
- More {% block %} tags in our base templates are better.
- Child templates don't have to define all parent blocks, so we can fill in reasonable defaults in a number of blocks, then only explain the ones we need later.
- We can't define multiple block tags with the same name in the same template.
- If We need to get the block's content from the parent template, the {{block.super}} variable will do the trick.

## Creating Base/Parent Template and Child Template:
- We write common codes in base template and create blocks for code which may vary page to page. Later this template will be inherited by child templates and child template will override created blocks.
-  If no block tags are specified in the child templtes then value is empty or the value written beside the block tag.
-  Use {{block.super}} to override the previous block
```python
(% block title %}
{{block.super}}
Home
{% endblock %}
```

```html
//Let's say that 2 pages have the same format just the title and the content inside the body changes.
// We first create a base.html:
// base.html
<html>
<head>
  <title>{% block title %} {% endbock %]</title>
</head>
  <body>
    {% block content %} {% endblock content %}
  </body>
</html>

// Then we create home.html, about.html and add whatever the content should be in the title and body
// home.html
{% extends 'base.html' %}
{% block title %}
Home                                // Adds Home to the base template title
{% endblock %}

{% block content %}
Hello I am Home Page                // Adds Hello I am Home page to the base template body
{% endblock content %}

// about.html
{% extends 'base.html' %}

{% block title %}
About                                // Adds Home to the base template title
{% endblock %}

{% block content %}
Hello I am About Page                // Adds Hello I am About page to the base template body
{% endblock content %}
```

### Create Hyperlinks:
##### Revisit [URL Dispatcher](https://github.com/IshaanAdarsh/TIL/blob/main/Django/Django_cc.md#url-dispatcher)
#### url Tag:
- `{% url %}`: It returns an absolute path reference (a URL without the domain name) matching a given view and optional parameters. Any special characters in the resulting path will be encoded using iri_to_uri.
```python
# Syntax
{% url 'uriname' %}
{% url 'urlname' as var %}
{% url 'urlname' arg1=valuel arg2=value2 %}
{% url 'urlname' valuel value2 %}
```

```python
# Easy Implementation:
urlpatterns = [
path('about/', views.about),
]

<a href="/about">About</a>          # Use / because

# Variable Implementation:

# Urls.py
urlpatterns = [
path('about/', views.about),
]

# Views.py
def about(request):
  return render(request, 'core/about.html', {'ab':'/about'})

<a href="{{ab}}">About</a>

# Using url tag:
urlpatterns = [ path('about/', views.about, name='aboutus'),]

# way1:
<a href="{% url 'aboutus' %}">About</a>

# way2(variable):
{% url 'aboutus' as abc %}
<a href="{{abc}}">About</a>

```

### How to include Template within Template:
-  To reduce clutter we use the include tag.

> For example, you need to add top courses on the website to the main site. But to not clutter the original html template we create another template named topcourse.html and use the include tag to add the contents on that template into the original template for more clean and understandable code.
#### Include tag:
- `{% include %}` Tag: It loads a template and renders it with the current context. This is a way of "including" other templates within a template. Each include is a completely independent rendering process.
- The template name can either be a variable or a hard-coded (quoted) string, in either single or double quotes.
```python
# Syntax:
{% include temp_var_name %}
{% include "template_name.html" %}
{% include "folder/template_name.html" %}

# Example:
{% include topvar %}
{% include "topcourse.html" %}
{% include "fees/extrafees.html" %}
```
- We can pass additional context explicitly to the template using with keyword.
```python
{% include "topcourse.html" with p="PHP" d="Django"%}
```
- If we want to render the context only with the variables provided (or even no variables at all), use the only option. No other variables are available to the included template.
```python
{% include "topcourse.html" with p="PHP" only %}
```

### Cookies:
- A cookie is a small text data set by a web server and stored on the client's machine.
- It is automatically sent back to the server with each request, allowing the server to store and access the information it wants to remember for the client.
- Cookies enable personalized responses and enhance user experience on websites.

#### Types of Cookies:
- **Session Cookies:** Cookies that are set without the expires field are called session cookies. It is destroyed when the user quits the browser.
- **Persistent Cookies:** The browser keeps it up until its expiration date is reached.

<hr>

# Model:
- A model is the single, definitive source of information about your data.It contains the essential fields and behaviors of the data you're storing. Each model maps to a single database table.

### Object Relational Mapper (ORM):
- It enables application to interact with databases, ORMs automatically create a database schema from defined classes or models. It generates SQL from Python code for a particular database which means developer do not need to write SOL Code.
  - ORM maps object attributes to respective table fields.
  - ORMs use connectors to connect databases with a web application.
- **QuerySet**
  - A list containing all those objects we have created using the Django model. QuerySets allow you to read the data from the database, filter it and order it.

## Model Class:
- Model class is a class which will represent a table in database.
  - Each model is a Python class that subclasses django.db.models.Model
  - Each attribute of the model represents a database field.
- Django gives you an automatically-generated database-access API. Django provides built-in database by default that is sqlite database.

### Create Our Own Model Class
- `models.py` file which is inside application folder, is required to create our own model class.
- Our own model class will inherit Python's Model Class.
- **Rule for Field_Name:**
  - It is a class attribute representing a table's column name, while Field Type denotes the data type. Field names cannot be Python-reserved words, contain consecutive underscores, or end with an underscore.

```python
# Syntax:
class ClassName(models.Model):
  field_name=models.FieldType(arg, options)

# Example:
# models.py
class Student(models. Model):
  stuid=models.IntegerField()
  # Length is required in CharField Type
  stuname=models.CharField(max_length=70)
  stuemail=models.EmailField(max_length=70)
  stupass=models.CharField(max_length=70)

python manage.py makemigrations
          |
          |
          |
          ↓
```
#### ORM produces:
```sql
CREATE TABLE "enroll student" (
  "id" integer NOT NULL PRIMARY KEY AUTOINCREMENT,
  "stuid" integer NOT NULL,
  "stuname" varchar(70) NOT NULL,
  "stuemail" varchar(70) NOT NULL,
  "stupass" varchar(70) NOT NULL
```
- This class will create a table with columns and their data types
- Table Name will be ApplicationName _ClassName, in this case it will be enroll student
- Field name will become table's Column Name, in this case it will be stuid, stuname, stuemail, stupass with their data type.
- As we have not mentioned the primary key in any of these columns so it will automatically create a new column named 'id' Data Type Integer with primary key and auto increment.

### How to use Models:
Once you have defined your models, you need to tell Django you will use those models.
- Open settings.py file
- Write app name which contains `models.py`, file in INSTALLED_APPS = []
- Open Terminal and run python manage.py makemigrations
- Run python manage. py migrate

### Migrations:
Migrations are Django's way of propagating changes you make to your models (adding a field, deleting a model, etc.) into your database schema.
- **makemigrations:** This is responsible for creating new migrations based on the changes you have made to your models. Used convert model class into sql statements. This will also create a file which will contain sql statements. This file is located in Application's migrations folder.
```python
Syntax:- python manage.py makemigrations
```
- **migrate:** This is responsible for applying and unapplying migrations. Used to execute sql statements generated by makemigrations. This command will execute All Application's (including built-in applications)

```python
Syntax:- python manage.py migrate
```

> Note: If you make any change in your own model class you are required to run makemigrations and migrate command only then you will get those changes in your application.

- **sqlmigrate:** This displays the SQL statements for a migration.

#### To Display SQL Statement:
```python
# Syntax:-
python manage.py sqlmigrate application name dbfile _ name

# Example:-
python manage.py sqlmigrate enroll 0001
```

<img width="1018" alt="migrations" src="https://github.com/IshaanAdarsh/TIL/assets/100434702/36bf4410-7973-4d9a-8e53-f90380caa60b">

- If we add a new field called comment in the original enroll file:

<img width="851" alt="Migration-dependencies" src="https://github.com/IshaanAdarsh/TIL/assets/100434702/d76532c0-7d29-4234-9a3c-e463b5ac01a3">

- More information about [Built-in Field Types](https://github.com/IshaanAdarsh/TIL/blob/main/Django/Detailed%20Information/Built-in%20Field%20Options.md)

- More information about [Model Operations](https://github.com/IshaanAdarsh/TIL/blob/main/Django/Detailed%20Information/Model-Operations.md)

- **showmigrations:** This lists a project's migrations and their status.

### Retrieve Database Table Data to User:
- Writing Code to get data from database in views.py then pass it to template files using render function
- Get Data which is passed by render function of views.py file in template file

#### all ()
- `all ()`: It returns a copy of the current QuerySet or QuerySet Subclass.
```python
# Syntax:
ModelClassName.obiects.all()
```

#### Steps: 
- First import your own model class from models.py
```python
# views.py
from enroll. models import Student def studentinfo(request):
stud = Student.objects.allo
return render(request, 'enroll/studetails.html', {'stu':stud})
```

- Get Data from views.py in template file
```html
templates/enroll/studetails.html
<!DOCTYPE HTML>
<html>
  <body>
    <h1>Student Page</h1>
    {% if stu %}
      <h1>Show Data</h1>
      {% for st in stu %}
          <h5> {{st.stuid}} </h5>
          <h5> {{st.stuname}} </h5>
      {% endfor %}
    {% else %}
      <h1>No Data</h1>
    {% endif %}
  </body>
<html>
```

## Admin Application
- It is a built-in application provided by Django.
- This application provides admin interface for CRUD operations without writing sq| statements.
- It reads metadata from your models to provide a quick, model-centric interface where trusted users can manage content on your site. Super User is required to login into Admin Application

#### Create Super User
- We need super user to login into admin interface of the admin application.
- createsuperuser command is used to create super user.
```python
python manage.py createsuperuser
```
- Admin Application can be accessed using `http://127.0.0.1:8000/admin`

- But the problem with using makemigration is that the db will not show up in the Admin panel until we register the model.

### How to Register Model:
We are registering our table which we has created using model class, to default admin interface.
To Register Follow:-
- Open admin py file which is inside Application Folder
- Import your own Model Class created inside Application's models.py
  - `from enroll. models import Student`
- admin.site.register(ModelClassName)
  - `admin.site.register(Student)`

### __str__() Method:
The __str__() method is called whenever you call str on an object. To display an object in the Django admin site and as the value inserted into a template when it displays an object. (human-readable representation of the model)
```python
# Write this Method in your own model class which is inside models.py file.
# Syntax:
def __str__(self):
  return self.fieldName

def __str__(self):
  return self.stuname
```

### ModelAdmin Class:
- The ModelAdmin class is the representation of a model in the admin interface. (All the data so as to not justify each field using __str__ funtion)
- To show table's all data in admin interface we have to create an ModelAdmin class in admin py file of Application folder.
```python
# Creating Class
Class ModelAdminClass Name(admin. ModelAdmin):
  class StudentAdmin(admin.ModelAdmin):

# ModelAdmin Options
list display=(fieldnamel', "fieldname2', .......)
  list_display-('id', 'stuid', 'stuname")
# Register Above Created Class
admin.site.register(ModelClass Name, ModelAdminClassName)
 admin.site.register(Student, StudentAdmin)
```

#### list_display
- Set list_display to control which fields are displayed on the change list page of the admin. If you don't set list _display, the admin site will display a single column that displays the __str__() representation of each object
- Must be a list or tuple, cannot contain only one value (use __str__ for that) or add it like ('fielname1',) [ADD a comma].

- There are four types of values that can be used in list display:
  - The name of a model field.
  - A callable that accepts one argument, the model instance.
  - A string representing a ModelAdmin method that accepts one argument, the model instance.
  - A string representing a model attribute or method (without any required arguments).

### Register Model by Decorator
- A decorator can be used to register ModelAdmin Classes.
- Syntax: `@admin.register(ModelClassNamel, ModelClassName2,.. ‚site=custom_admin_site)`

#### Procedure:
```python
# Register Model Classes
@admin.register(ModelClassName)
  @admin. register(Student)
# Creating Class
Class ModelAdminClass Name(admin.ModelAdmin):
list display ('fieldnamel', 'fieldname2', ......
  class StudentAdmin(admin. ModelAdmin):
  list_display -('id', 'stuid', 'stuname")
```

## Diango Form (Form API):
- Django's form functionality can simplify and automate vast portions of work like data prepared for display in a form, rendered as HTML, edit using a convenient interface, returned to the server, validated and cleaned up etc and can also do it more securely than most programmers would be able to do in code they wrote themselves.
- Django handles three distinct parts of the work involved in forms:
  - preparing and restructuring data to make it ready for rendering
  - creating HTML forms for the data
  - receiving and processing submitted forms and data from the client

### Bound and Unbound Forms
- If it's bound to a set of data, it's capable of validating that data and rendering the form as HTML with the data displayed in the HTML.
- If it's unbound, it cannot do validation (because there's no data to validate!), but it can still render the blank form as HTML.

### Create Diango Form using Form Class
- To create Django form we have to create a new file inside application folder lets say file name is forms.py.
- Now we can write below code inside forms.py to create a form:

```python
# forms.py
# Syntax:
from django import forms
class FormClassName(forms.Form):
  label=forms.FieldType0
  label=forms.FieldType(label='display label')

# Example:
from django import forms
class StudentRegistration(forms. Form):
  name=forms.CharField()                        # Here length is not required
  email=forms.EmailField()
              |
              |
              |
              ↓
```
```html
<tr>
  <th> <label for="id name">Name:</label> </th>
  <td> <input type="text" name="name" required id="id name"> </td>
</tr>
<tr>
  <th> <label for="id email">Email:</label> </th>
  <td><input type="email" name="email" required id="id email"></td>
<tr>
```

#### Display Form to User
- Create an object of Form class in views.py then pass object to template files
- Use Form object in template file

#### Creating Form obiect in views.py
- Create form object inside views.py file then pass this object to template file as a dict.
```python
# views.py
from .forms import StudentRegistration
def showformdata(request):
  fm = StudentRegistration
  return render(request, 'enroll/userregistration.html',{'form':fm})
```
> Form object won't provide form tag and button you have to write them manually in template file.

#### Get object from views.py in template file:
```html
// templates/enroll/userregistration.html
<!DOCTYPE html>
<html>
  <body>
    // {{form}} doesn't add form tag and button so we have to add them manually.
    <form action ="" method="get">
      {{form}}
      <input type="submit" value="Submit">
    </form>
  </body>
</html>
```

#### Form Rendering Options
- {{form}} will render them all
- {{ form.as table }} will render them as table cells wrapped in <tr> tags
- {{ form.as_p}} will render them wrapped in <p> tags
- {{ form.as ul}} will render them wrapped in <li> tags
- {{ form.name of field }} will render field manually as given

### Render Form Field Manually:
- Each field is available as an attribute of the form using `{{form.name_of_field}}`
```html
// The label of the field.
{{ field.label }}
Example: - {{ form.name.label }}      // in name field the label is returned

// The field's label wrapped in the appropriate HTML <label> tag. This includes the form's label suffix. The default label suffix is a colon:
{{ field .label _tag }}
Example: - {{ form.name.label_tag }}

// The ID that will be used for this field.
{{ field.id_for_label }}
Example:- {{form.name.id_for_label }}

// The value of the field.
{{ field.value }}
Example: - {{ form.name.value }}

// The name of the field that will be used in the input element's name field. This takes the form prefix into account, if it has been set.
{{ field.html_name }}
Example:- {{ form.name.html_name }}

// Any help text that has been associated with the field.
{{ field.help_text }}
Example:- {{ form.name.help_text }}

// The Field instance from the form class that this BoundField wraps. You can use it to access Field attributes.
{{ field field }}
Example:- {{form.name.field.help_text}}

// This attribute ({{ field.is_hidden }}) is True if the form field is a hidden field and False otherwise. It's not particularly useful as a template variable but could be useful in conditional tests such as:
{% if field.is hidden %}
  {# Do something special #}
{% endif %}
```
### Configure id attribute:
- `auto_id`: The id attribute values are generated by prepending id_ to the form field names. This behaviour is configurable, though, if you want to change the id convention or remove HTML id attributes and <label> tags entirely.
- Use the auto_id argument to the Form constructor to control the id and label behaviour. This argument must be True, False or a string. By default, auto_ id is set to the string 'id_%s'.

- **auto_id == True:** then the form output will include <label> tags and will use the field name as its id for each form field. Also if auto_id is set to any other true value - such as a string that doesn't include % - then the library will act as if auto id is True.

```python
# Views.py
# Particular string output 
from .forms import StudentRegistration
def showformdata(request):
  # Changes the auto_id to a string format -> some_(name)
  fm = StudentRegistration(auto_id = 'some_%s')                     
  return render(request, 'enroll/userregistration.html',{'form':fm})

# We want the same name as the attribute declared
# Method 1: Set auto_id to True
from .forms import StudentRegistration
def showformdata(request):
  # Both label and id values are changed to the name provided as the attribute name
  fm = StudentRegistration(auto_id = True)                     
  return render(request, 'enroll/userregistration.html',{'form':fm})

# Method 2: Set the value to any string literal
from .forms import StudentRegistration
def showformdata(request):
  # Both label and id values are changed to the name provided as the attribute name (Not ishaan)
  fm = StudentRegistration(auto_id = 'ishaan')                     
  return render(request, 'enroll/userregistration.html',{'form':fm})
```

- **auto_id == False:** If auto_id is False, then the form output will not include <label> tags nor id attributes. Also if auto_id is set to a string containing the format character '%', then the form output will include <label> tags and will generate id attributes based on the format string. 

```python
# views.py
# If we set auto_id to false then the label tag and id attribute gets removed
from .forms import StudentRegistration
def showformdata(request):
  # Both label and id values are changed to the name provided as the attribute name (Not ishaan)
  fm = StudentRegistration(auto_id = False)                     
  return render(request, 'enroll/userregistration.html',{'form':fm})
```

### Configure Label attributes:
- `label suffix`: A translatable string (defaults to a colon (:) in English) that will be appended after any label name when a form is rendered.
- It's possible to customize that character, or omit it entirely, using the label suffix parameter. The label suffix is added only if the last character of the label isn't a punctuation character (in English, those are , !,? or :)

```python
# Views.py
# This adds a - to the main form output (Name[TEXT_BOX] -> Name-[TEXT_BOX])
fm = StudentRegistration(label suffix = '-')
```

### Dynamic Initial Values:
- `initial`: It is used to declare the initial value of form fields at runtime.
- To accomplish this, use the initial argument to a Form. This argument, if given, should be a dictionary mapping field names to initial values. Only include the fields for which you're specifying an initial value. It's not necessary to include every field in your form.
- If a Field defines initial and you include initial when instantiating the Form, then the latter initial will have precedence.
```python
# Views.py
# Adds predifined value to the text box the the id mentioned
fm = StudentRegistration(auto_id = 'some_%s', label suffix = '-', initial = {'name': 'Ishaan'})
```

> Tip: If we declare the name of the form in the forms.py file as first_last, it auto matically converts the form label into 'first last'. The underscores are removed to fill with white spaces.

### Ordering Form Field:
- `order_fields(field _order)`: This method is used to rearrange the fields any time with a list of field names as in field _order. By default `Form.field order=None`, which retains the order in which you define the fields in your form class.
- If field order is a list of field names, the fields are ordered as specified by the list and remaining fields are appended according to the default order. Unknown field names in the list are ignored.
```python
# views.py
from .forms import StudentRegistration
def showformdata(request):
  fm = StudentRegistration()
  fm.order_fields(field_order= ['email', 'name'])
```

### Loop Form Fields and Form Hidden Fields
- Access the various fields for the form using for loop (not doinf individually)
```html
// This prints out all the labels for the form elements
<form action="" method="get">
  {% for field in form %}
    {{field.label_tag}}
  {% endfor %}
<input type="submit" value="Submit">
</form>

// This prints only the visible labels of the form elements
<form action="" method="get">
  {% for hidden in form.hidden_fields %}
    {{hidden}}
  {% endfor %}
<input type="submit" value="Submit">
</form>
```

### Form Field
- A form's fields are themselves classes; they manage form data and perform validation when a form is submitted.
- `Syntax:- FieldType(**kwargs)`
```python
# forms.py
IntegerField()
CharField(required)
CharField(required, widget="Textarea')

# Proper way to integrated the form
from django import forms
class StudentRegistration(forms. Form):
name = forms.CharField()
```

### Field Arguments
- `required`: It takes a True or False value. By default, each Field class assumes the required value is True.
- `label`: The label argument lets you specify the "human-friendly label for the field. This is used when the Field is displayed in a Form.
- `label _suffix`: The label suffix argument lets you override the form's label suffix on a per-field basis.
- `initial`: The initial argument lets you specify the initial value to use when rendering this Field in an unbound Form.
- `disabled`: The disabled boolean argument, when set to True, disables a form field using the disabled HTML attribute so that it won't be editable by users. Even if a user tampers with the field's value submitted to the server, it will be ignored in favor of the value from the form's initial data.
- `help_text`: The help _text argument lets you specify descriptive text for this Field. If you provide help_text, it will be displayed next to the Field when the Field is rendered.
- `error_messages`: The error messages argument lets you override the default messages that the field will raise. Pass in a dictionary with keys matching the error messages you want to override.
- `validators`: The validators argument lets you provide a list of validation functions for the field.
- `localize`: The localize argument enables the localization of form data input, as well as the rendered output.

### `widget`: 
- The widget argument lets you specify a Widget class to use when rendering the Field.
- A widget is Django's representation of an HTML input element.
- The widget handles the rendering of the HTML, and the extraction of data from a GET/POST dictionary that corresponds to the widget. The HTML generated by the built-in widgets uses HTMLS syntax, targeting <!DOCTYPE html>.
- Whenever you specify a field on a form, Django will use a default widget that is appropriate to the type of data that is to be displayed. Each field type has an appropriate default Widget class, but these can be overridden as required.
- Form fields deal with the logic of input validation and are used directly in templates.
- Widgets deal with rendering of HTML form input elements on the web page and extraction of raw submitted data.
- `TextInput`, `Textarea`

#### attrs 
- A dictionary containing HTML attributes to be set on the rendered widget. If you assign a value of True or False to an attribute, it will be rendered as an HTMLS boolean attribute.
```python
feedback-forms.CharField(widget-forms.TextInput(attrs={'class':'somecss1somecss2'
'id':'uniqueid'")
```
```python
# forms.py
from django import forms
# In this the label of the form element is changed from `Name:` to `Your Name `, the prevalue is set to sonam and the field is not required to be filled as the required is false. Help text creates a separate text box with a class helpbox hich can be further updated by CSS.
class StudentRegistration (forms.Form) :
  name = forms. CharField{Label='Your Name', Label_suffix=' ', initial='Sonam', required=False, disabled=True, help_text= 'Limit 70 Char")

# error_message
name=forms.CharField(error messages={'required': 'Enter Your Name' })
```

### GET method vs POST method:
```html
<form method = "get">
</form>

<form method = "post">
</form>
```
#### GET Method:
- GET should be used only for requests that do not affect the state of the system.
- GET, by contrast, bundles the submitted data into a string, and uses this to compose a URL. The URL contains the address where the data must be sent, as well as the data keys and values.
- GET would also be unsuitable for a password form, because the password would appear in the URL, and thus, also in browser history and server logs, all in plain text. Neither would it be suitable for large quantities of data, or for binary data, such as an image. A Web application that uses GET requests for admin forms is a security risk: it can be easy for an attacker to mimic a form's request to gain access to sensitive parts of the system.
- GET is suitable for things like a web search form, because the URLs that represent a GET request can easily be bookmarked, shared, or resubmitted.

#### POST Method:
- Any request that could be used to change the state of the system should use POST.
- POST, coupled with other protections like Django's CSRF protection offers more control over access.
- Django's login form is returned using the POST method, in which the browser bundles up the form data, encodes it for transmission, sends it to the server, and then receives back its response.

## Cross Site Request Forgery (CSRF/ XSRF):
- A Cross-site request forgery hole is when a malicious site can cause a visitor's browser to make a request to your server that causes a change on the server. The server thinks that because the request comes with the user's cookies, the user wanted to submit that form.

### Create form using POST method:
- If we use GET then the information fed into the form is shown in the URL which causes security issues.
- So we use POST method:
  - We set the method to `post` and we include a CSRF token int the form to verify the form

#### Cross Site Request Forgery (CSRF) Token:
- Django provides CSRF Protection with csrf_token which we need to add inside form tag. This token will add a hidden input field with random value in form tag. 
```html
// templates/enroll/userregistration.html
<!DOCTYPE html>
<html>
  <bodv>
    <form method="post"> 
      {% csrf_token %}
      <input type="submit" value="Submit">
    </form>
  </body>
</html>
``` 
