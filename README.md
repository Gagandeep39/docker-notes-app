# Notes

## Description

- NodeJS REST backend
- React Frontend
- 3 Containers for Database, frontend, backend will be used

## Steps to Run

### MongoDB database

1. `docker run --name mongodb -p 27017:27017 --rm -d mongo` Run mongoDB image

### NodeJS server

1. `docker build -t goal-server:1 .` Create Image
2. `docker run --rm -p 8000:8000 --name goal-server-container goal-server:1` Run Image

### Frontend

1. `docker build -t goal-frontend:1 .` Create Image
2. `docker run --rm -p 3000:3000 -it --name goal-frontend-container goal-frontend:1` Run Image (React apps must be ran in interactive mode)

## NOTE
- In react container we are not using host.docker,internal because the requests will be sent from localhost and not from inside cotnainer.
- React code serves Javascript files that are served to user and then from users PC requests are made
