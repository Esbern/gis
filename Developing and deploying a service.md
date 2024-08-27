---
title: Developing and deploying a service
draft: false
tags:
---
 
In this demo, I will show how to create a simple Python web app using plotly dash in a docker container. The trick here is that the container has two "states" set at build time: one for development, where the container starts and waits for the developer IDE to connect, and one for deployment.
 This setup is a simple folder on the host computer with the following content :
 .
`├── app/`
`│   ├── __init__.py`
`│   ├── app.py`
`│   └── layouts.py`
`├── Dockerfile`
`├── docker-compose.yml`
`├── entrypoint.sh`
`└── requirements.txt`
 The app subfolder contains the code for the application the conten of the files are simply :
 
 **app/__init__.py**
```
from dash import Dash
app = Dash(__name__)
from app import layouts  # Import layouts after the app is created

```
 **app/app.py**
```
 from app import app  # Import the app instance from __init__.py

if __name__ == '__main__':
    app.run_server(debug=True, host='0.0.0.0')`
```

**app/layouts.py**
```
from dash import html
from app import app

app.layout = html.Div(children=[
    html.H1(children='Hello Dash'),
    html.Div(children='''Dash: A web application framework for Python.'''),
])
```

The **requirements.txt** file
This file simply specifies which libraries are to be installed in the container environment, in this case using pip install in the Docker file 

requirements.txt
`dash`

**Dockerfile**
The docker file is the code that defines the "container" and its contents
```
# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Set a working directory
WORKDIR /app

# Install dependencies
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Copy the entrypoint script and give it execute permissions
COPY entrypoint.sh /app/entrypoint.sh
RUN chmod +x /app/entrypoint.sh

# Copy the application code
COPY ./app /app/app

# Set the entrypoint script
ENTRYPOINT ["/app/entrypoint.sh"]
```

**Entrypoint Script**
The entrypoint.sh is a simple bash script that is run when the container is starting the role of the script is to ensure that the container starts differently depending on wheater it is in development or deployment model.
```
#!/bin/bash

if [ "$ENV" = "development" ]; then
    echo "Starting in development mode..."
    while true; do sleep 1; done  # Keeps the container running so you can attach VSCode
else
    echo "Starting in production mode..."
    exec python -m app.app  # Note the updated path for running the app
fi
```

**docker-compose**
the docker-compose.yml file defines who the container is running, including which network and ports to use and dependencies on other containers. In this example, there are no other containers and nn internal network the port is the external port by wich the service can be reached:

docker-compose.yml

```
services:
  dash-app:
    build:
      context: .
    environment:
      - ENV=development  # Change to 'production' for production builds
    volumes:
      - .:/app  # Mount your source code
    ports:
      - "8050:8050"  # Dash's default port
    tty: true  # Keeps the container running to attach VSCode
```

**Starting and running the container**

from the command line in the folder, you can now run:
`docker-compose -f docker-compose.yml up --build -d`

If you are using docker desktop, you can see the running container 
![[docker-demo.png]]
In your IDE (in this case, VS code), you can attach to the running container so it becomes the development environment
![[vs code attach docker container.png]]