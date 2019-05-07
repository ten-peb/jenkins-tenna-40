FROM ubuntu-nodejs-8:0.5.0
MAINTAINER Peter L. Berghold <pberghold@tenna.com>

EXPOSE 80

WORKDIR /var/www/html

RUN mkdir public 
COPY ui/node_modules/ ./node_modules/
COPY ui/server.js ./

RUN npm install
RUN npm cache clean --force


# CMD ["node","server.js"]

COPY entrypoint.sh /entrypoint.sh
RUN chmod 755 /entrypoint.sh

ENTRYPOINT /entrypoint.sh
