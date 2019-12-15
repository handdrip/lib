---
layout: post
title: "Laradock PM2 추가하기"
date: 2019-12-15T10:48:00+09:00
tags: [laradock, nodejs, pm2]
image: "/images/posts/pm2.png"
---

##### pm2
Laradock에는 pm2가 기본적으로 추가되어 있지 않다.

간략하게 pm2를 laradock에 설정하는 방법을 기록한다.

###### 1. Laradock env의 workspace install 목록에 pm2를 추가한다.
```sh
WORKSPACE_INSTALL_NPM_PM2=true
```

###### 2. docker-compose.yml에도 마찬가지로 workspace에 pm2 추가한다.
```sh
WORKSPACE_INSTALL_NPM_PM2=true
```

###### 3. workspace - Dockerfile pm2 설정
```sh
ARG INSTALL_NPM_PM2=false
```

```sh
&& if [ ${INSTALL_NPM_PM2} = true ]; then \
npm install pm2@latest -g \
;fi \
```

###### 4. 설정후 workspace rebuild.
```sh
docker-compose build workspace
```

이후 workspace 컨테이너를 다시 띄우고 pm2 명령어를 실행하면 포스트의 이미지와 같은 결과를 확인할 수 있다.
