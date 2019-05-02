FROM ubuntu-nodejs-8:0.5.0
MAINTAINER Peter L. Berghold <pberghold@tenna.com>

EXPOSE 80

WORKDIR /var/www/html

COPY ui/public ./public
COPY ui/server.js ./

RUN npm install
RUN npm cache clean --force


CMD ["node","server.js"]
