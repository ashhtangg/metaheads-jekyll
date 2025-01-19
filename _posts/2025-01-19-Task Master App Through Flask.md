---
category: doc
tags: [python, flask]
---

## Intro 

So I wanted to start learning to make web-apps, since I've been learning Python, it made sense that I were to use a framework that was related to Python to start with.

I started with a task master since I want to learn setting static content, but also a simple way where I can use SQL to store/commit information

## Virtual Enviroment 

I first created a virtual enviroment, this is so that later I can freeze the requirments when I push it into Heroku for reference, as it allows me to exclusively show the used packages for the project

I done through `virtualenv env` you can technically use any name after `virtualenv` however I thought to keep it `env` to make it simple.

### Entering the Virtual Enviroment and installing Relevant Packages

I then used `.\env\Scripts\activate.ps1` to enter into the virtual enviroment and start working 

I intalled the required packes through  `pip flask and flasksqlalchemy`.

## Basic Flask Deployment

```
#imports
from flask import Flask

#__name__ references this file
app = Flask(__name__)

@app.route('/')
def index():
    return 'Hello, World!'

if __name__ == "__main__":
    app.run(debug=True)
```

This is the basic flask deployment, you would typically create a file called 'app.py' and follow the above.

`from flask import Flask` 
This imports the package that I need for this (Flask)

`app = Flask(__name__)` 
Assigns this file as the app that runs, `(__name__)` signifies this file's name

```
@app.route('/')
def index():
    return 'Hello, World!'
```
`@app.route('/')`
This is how Flasks links/makes directories for your webpage, `/` means that this is located at the root directly of your webapp

```
def index():
    return 'Hello, World!'
```
This is a function beneath it that shows what that directory does, for this example, it just returns/prints 'Hello, World!'

```
if __name__ == "__main__":
    app.run(debug=True)
```
The final part of the template, if __name__ equals __main__, the app will run and debug is enabled for you to review errors, any file that is run within Python, the file converts into __main__ which is why this works.


## Making a Template and Template Inheritance 

So you'll need to create an HTML file to link to the function under `app.route`, you first awant to make an 'index.html', use an exclamation mark within VSCode so that you can get the generic HTML tempalte quicker

### render_template

You want to use this function to render/load the html template after yor 'app.route', under your previous function, do `return render_template('index.html')`

So it should look like this 

```
@app.route('/')
def index():
    return render_template('index.html')
```

You'll also have to add the 'return_template' function with your imports, and of course fill in your HTML file has desired. 

### Template Inheritance Part 1 

What this does is that it allows you to refer to one HTML file as the 'master file' so that you don't have to copy the same HTML template every time. Make sure to create a 'templates' folder and place your HTML files within here. 

How this works is that you have to use blocks, the syntax for this is `{% block 'x' %} {% endblock %}`. The `{}` is a way to use python logic within HTMl or other files.

This syntax is specifcally for template inheritance. 

You want to place these blocks within your HTML where you would want works changed, for example the header, or the body of the HTML.

### Template Inheritance Part 2

After you done this, you want to create other HTML files and refer/extend back to the master. You do this  through `{% extends 'base.html' %}`

You'll then refer back to the blocks within your base/master html, and change it like so

```
{% block head %}
<h1>Example</h1>
{% endblock %}
```

## Linking CSS 

Since this is just bare HTML files, it'll look quite plain, so you would link your CSS file for styling.

Create a folder named 'static' and place your 'main.css' within here. From there change your CSS file to how you see fit and you can link it through the below 

For this example, I just removed margins and change the font that's used for the next on the body

```
body{
    margin:0;
    font-family: sans_serif;
}
```

### Linking CSS in HTML file 

You would link it through placing this in the head of your HTMl `<link rel="stylesheet" href="{{url_for('static', filename='css/main,css)}}}">`

The `<link>` tag is used to link to external resource, in this case it refers to the CCS file, `rel="stylesheet"` specifies the relationship between the current document and the linked resource, for this example we used 'stylesheet' `href` refers to the location of the linked document 

`{{url_for('static', filename='css/main.css')}}`: This is a server-side template expression, likely using Jinja2 templating language often used with Flask:
url_for() is a Flask function that generates URLs
'static' refers to the static folder in Flask's directory structure
filename='css/main.css' specifies the path to the CSS file within the static folder