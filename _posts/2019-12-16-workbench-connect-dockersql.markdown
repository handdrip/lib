---
layout: post
title: "Laradock sql workbench (or other database sw;) 연결"
date: 2019-12-16T14:40:00+09:00
tags: [laradock, mysql, mariadb, workbench]
image: "/images/posts/workbench-laradock.jpg"
---

```bash
Hostname: 0.0.0.0
```

laradock sql 컨테이너에 workbench 등의 database 툴로 연결하려면 Hostname을 0.0.0.0으로 설정하는 것이 중요하다.
나머지 port는 env상에서 설정한대로, username은 laradock sql에 생성(설정)한 계정을 이용하면 된다.
