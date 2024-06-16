FROM node

WORKDIR /app

COPY ./package.json /app

RUN npm install

COPY . .

ENV MONGODB_USERNAME=admin
ENV MONGODB_PASSWORD=secret

EXPOSE 80

CMD [ "npm", "start" ]