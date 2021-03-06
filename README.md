# https://github.com/minhnc12/fenvbox

This is the Git repo of the DOCKER NGINX-NODEJS 12.x


# Tutorial

Follow these steps to deploy:

## Start FE with docker-compose.yml

Step 1
```
vim docker-compose.yml
```
Copy and save the following:

```
version: '3'
services:
  app:
    image: w2s12/fenvbox:1.0
    ports:
      - 8000:80
    depends_on:
      - db
    volumes:
      - .:/usr/src/app
      - ./demo/build:/usr/share/nginx/html:ro
      - ./conf/nginx.conf:/etc/nginx/sites-available/default
   #working_dir: /usr/src/app/demo
    command:
    - /bin/bash
    - -c
    - |
      service nginx restart
      tail -f /dev/null 2>&1
    restart: on-failure
  ...

```

Assuming all steps were followed correctly, this will pull all the required images and start serving the app:
```
docker-compose up -d
```

NOW, We can access this with localhost:8000 for FE

# Contributing


# License
MIT