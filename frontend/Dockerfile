FROM node:alpine
LABEL authors="Gagandeep Singh"
WORKDIR /app
COPY package.json /app
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
