# 作業 - 4. 透過 docker 部署開發環境

用 docker compose 把服務跑起來

## Dockerfile

```
FROM node:18

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

CMD [ "node", "dist/main.js" ]
```

## docker-compose.yml

沒有 image 的話會先 build

```
services:
  web:
    build: .
    image: sam/smms_day1-4
    container_name: smms_day1-4
    ports:
      - '4000:3000'
```

## Command

都會根據當前目錄的 docker-compose.yml 執行

```
sudo docker compose up -d
sudo docker compose stop
sudo docker compose rm
```
