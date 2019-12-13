---
layout: post
title: Swagger 사용하기
subtitle: API Endpoint 
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,flask,swagger]
---

# Python REST APIs With Flask, Connexion, and SQLAlchemy
- 해당 내용은 [Real Python](https://realpython.com/flask-connexion-rest-api/#demonstration-single-page-application) 컨텐츠 리뷰 및 테스트한 내용을 정리한 것입니다.

## Getting started

> server.py

```python
from flask import (
    Flask,
    render_template
)

# Create the application instance
app = Flask(__name__, template_folder="templates")

# Create a URL route in our application for "/"
@app.route('/')
def home():
    """
    This function just responds to the browser ULR
    localhost:5000/

    :return:        the rendered template 'home.html'
    """
    return render_template('home.html')

# If we're running in stand alone mode, run the application
if __name__ == '__main__':
    app.run(debug=True)
```

> home.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Application Home Page</title>
</head>
<body>
    <h2>
        Hello World!
    </h2>
</body>
</html>
```

> shell

```shell
$ python server.py
```

## Using Connexion to Add a REST API Endpoint
> swagger ui를 사용하려면
```shell
$ pip install connexion # real python 가이드대로 하면 이 모듈 설치시 UI 사용 불가
$ pip install connexion[swagger-ui] # https://connexion.readthedocs.io/en/latest/quickstart.html
```

## Adding Connexion to the Server

```python
from flask import render_template
import connexion

# Create the application instance
app = connexion.App(__name__, specification_dir='./')

# Read the swagger.yml file to configure the endpoints
app.add_api('swagger.yml')

# Create a URL route in our application for "/"
@app.route('/')
def home():
    """
    This function just responds to the browser ULR
    localhost:5000/
    :return:        the rendered template 'home.html'
    """
    return render_template('home.html')

# If we're running in stand alone mode, run the application
if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000, debug=True)
```

## Swagger YAML 추가

```yaml
swagger: "2.0"
info:
  description: This is the swagger file that goes with our server code
  version: "1.0.0"
  title: Swagger REST Article
consumes:
  - "application/json"
produces:
  - "application/json"

basePath: "/api"

# Paths supported by the server application
paths:
  /people:
    get:
      operationId: "people.read"
      tags:
        - "People"
      summary: "The people data structure supported by the server application"
      description: "Read the list of people"
      responses:
        200:
          description: "Successful read people list operation"
          schema:
            type: "array"
            items:
              properties:
                fname:
                  type: "string"
                lname:
                  type: "string"
                timestamp:
                  type: "string"
```

## Swagger와 연동하는 엔드포인트 핸들러 추가

```python
from datetime import datetime

def get_timestamp():
    return datetime.now().strftime(("%Y-%m-%d %H:%M:%S"))

# Data to serve with our API
PEOPLE = {
    "Farrell": {
        "fname": "Doug",
        "lname": "Farrell",
        "timestamp": get_timestamp()
    },
    "Brockman": {
        "fname": "Kent",
        "lname": "Brockman",
        "timestamp": get_timestamp()
    },
    "Easter": {
        "fname": "Bunny",
        "lname": "Easter",
        "timestamp": get_timestamp()
    }
}

# Create a handler for our read (GET) people
def read():
    """
    This function responds to a request for /api/people
    with the complete lists of people

    :return:        sorted list of people
    """
    # Create the list of people from our data
    return [PEOPLE[key] for key in sorted(PEOPLE.keys())]
```