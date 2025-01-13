FROM node:16-alpine

# 必要なビルドツールをインストール
# この行を追加: AlpineにPython、make、g++をインストール
RUN apk add --no-cache python3 make g++ && \
    python3 -m ensurepip && \
    pip3 install --no-cache --upgrade pip

COPY . /home/node/webapp

RUN cd /home/node/webapp; \
    mv docker-entrypoint.sh /usr/local/bin; \
    chmod +x /usr/local/bin/docker-entrypoint.sh; \
    npm install;

ENV MYSQL_HOST="127.0.0.1"
ENV MYSQL_PORT="3306"
ENV MYSQL_USERNAME="YOUR-MYSQL-USERNAME"
ENV MYSQL_PASSWORD="YOUR-MYSQL-PASSWORD"
ENV MYSQL_DATABASE="tastylog"

EXPOSE 3000

WORKDIR /home/node/webapp
ENTRYPOINT [ "docker-entrypoint.sh" ]
CMD [ "npm", "start" ]