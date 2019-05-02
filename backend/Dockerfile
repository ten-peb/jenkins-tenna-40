FROM ubuntu-nodejs-8:0.5.0
MAINTAINER  Peter L. Berghold <pberghold@tenna.com>

WORKDIR /opt/tenna-crud
COPY ./backend/package.json /opt/tenna-crud/package.json
COPY ./backend/app/ /opt/tenna-crud/app/
COPY ./backend/config/ /opt/tenna-crud/config/

RUN npm install --quiet

EXPOSE 3000

CMD ["node","/opt/tenna-crud/app/www"]

