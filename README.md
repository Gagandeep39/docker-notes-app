# Notes

## Description

- NodeJS REST backend
- React Frontend
- 3 Containers for Database, frontend, backend will be used

## Building Images

- Always make Image after changing hostnames
- `docker build -t goal-server:1 .` Create backend image
- `docker build -t goal-frontend:1 .` Create frontned image

## Steps to Run - Method 1

### MongoDB database

1. `docker run --name mongodb -p 27017:27017 --rm -d mongo` Run mongoDB image

### NodeJS server

1. Update mongodb pport to `docker.internal.host:27017`
2. `docker build -t goal-server:1 .` Create Image
3. `docker run --rm -p 8000:8000 --name goal-server-container goal-server:1` Run Image
4. Run using method 2 first (Will not require any changes), as the code contains hardcoded IPs.

### Frontend

1. Make sure server hostname to send request is `localhost:8000`
1. `docker build -t goal-frontend:1 .` Create Image
2. `docker run --rm -p 3000:3000 -it --name goal-frontend-container goal-frontend:1` Run Image (React apps must be ran in interactive mode)

## NOTE
- In react container we are not using host.docker,internal because the requests will be sent from localhost and not from inside cotnainer.
- React code serves Javascript files that are served to user and then from users PC requests are made

## Steps to Run - Method 2

1. `docker network create goals-network`
2. `docker run --name mongodb --network goals-network --rm -d mongo`
3. Update hostname in backend code as `mongodb:27017`
4. `docker run --rm --network goals-network -p 8000:8000 --name goal-server-container goal-server:1` Run Image
5. Update hostname in frontend to `localhost:8000`
6. `docker run --rm -p 3000:3000 --network goals-network -it --name goal-frontend-container goal-frontend:1`

### NOTE
- Frontend code will run static code on browser, even though it is a part of network, requests sent from frontend cant use docker image name, it must use locahost. Server must expose its port number to be accessed by frontend
