FROM node:lts-alpine

RUN npm install -g http-server

WORKDIR /var/www/

COPY package*.json /var/www/

RUN npm install

COPY . /var/www/

EXPOSE 5173

CMD ["npm", "run", "dev"]