#FROM ubuntu:latest
#
#WORKDIR /var/www
#
#RUN apt-get update && \
#    apt-get install -y curl nano  \
#    && rm -rf /var/lib/apt/lists/*
#
#COPY ../ /var/www
#
#RUN curl -fsSL https://deb.nodesource.com/setup_22.x | bash - \
#     && apt-get install -y nodejs \
#     && npm install -g npm
#
#ENTRYPOINT ["top", "-b"]

FROM node:lts-alpine

RUN npm install -g http-server

WORKDIR /var/www/

COPY package*.json /var/www/

RUN npm install

COPY . /var/www/

RUN npm run build

EXPOSE 5173

CMD ["npm", "run", "dev"]