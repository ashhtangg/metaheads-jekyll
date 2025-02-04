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