FROM node:6

RUN mkdir -p /home/node/ && apt-get update && apt-get -y install curl
COPY ./app/ /home/node/app/
ADD test.txt /home/node
ENV AWS_SECRET_KEY="1234q38rujfkasdfgws"
