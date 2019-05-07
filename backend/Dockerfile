FROM ubuntu-nodejs-8:0.5.0
MAINTAINER  Peter L. Berghold <pberghold@tenna.com>

WORKDIR /opt/tenna-crud
COPY ./backend/package.json /opt/tenna-crud/package.json
COPY ./backend/app/ /opt/tenna-crud/app/
# COPY ./test /opt/tenna-crud/test/
COPY .env.sample .env
COPY .docker.env.sample .docker.env
COPY .sequelizerrc .sequelizerrc 


RUN npm install --quiet

EXPOSE 3000

ENV WAITFORIT_VERSION="v2.4.1"
ENV GITHUB_REPO="https://github.com/maxcnunes"
ENV WAIT4IT="waitforit-linux_amd64"
ENV REL_PATH="/waitforit/releases/download/${WAITFORIT_VERSION}/${WAIT4IT}"
ENV WAIT4ITURL="${GITHUB_REPO}/${REL_PATH}"
RUN curl -o /usr/local/bin/waitforit -sSL  ${WAIT4ITURL} && \
    chmod +x /usr/local/bin/waitforit

CMD ["node","/opt/tenna-crud/app/www"]

