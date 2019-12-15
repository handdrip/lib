---
layout: post
title: "Node/Express js bcrypt error"
date: 2019-12-15T23:05:00+09:00
tags: [error, nodejs, express, bcrypt]
image: "/images/posts/1.jpg"
---

##### problem: node 서버 실행시 아래와 같은 에러 발생

```javascript
internal/modules/cjs/loader.js:1197
  return process.dlopen(module, path.toNamespacedPath(filename));
                 ^
Error: /var/www/portfolio/app/node_modules/bcrypt/lib/binding/bcrypt_lib.node: invalid ELF header
```

##### solution

```bash
npm rebuild bcrypt --build-from-source
```

##### refrences

https://github.com/kelektiv/node.bcrypt.js/issues/635
