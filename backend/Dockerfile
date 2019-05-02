FROM ubuntu-nodejs-8:0.5.0
MAINTAINER  Peter L. Berghold <pberghold@tenna.com>

WORKDIR /opt/tenna-crud
COPY ./package.json /opt/tenna-crud/package.json
COPY ./app/ /opt/tenna-crud/app/
COPY ./config/ /opt/tenna-crud/config/

RUN npm install --quiet

EXPOSE 3000

CMD ["node","/opt/tenna-crud/app/www"]

