FROM node:alpine
LABEL authors="Gagandeep Singh"
WORKDIR /app
COPY package.json /app
RUN npm install
COPY . .
EXPOSE 80
CMD ["node", "app.js"]
