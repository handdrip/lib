---
layout: post
title: "Laradock + VSCODE + XDEBUG (MAC OS) 설정"
date: 2020-01-12T19:05:00+09:00
tags: [laradock, xdebug, php]
image: "/images/posts/xdebug.png"
---

#### 1. .env xdebug 설정

```bash
WORKSPACE_INSTALL_XDEBUG=true
...
PHP_FPM_INSTALL_XDEBUG=true
```

#### 2. xdebug.ini

- workspace / xdebug.ini
- php-fpm / xdebug.ini

```bash
xdebug.remote_host=docker.for.mac.localhost # 만약 window OS라면 mac => win
xdebug.remote_connect_back=0
xdebug.remote_port=9004 # port 설정은 알아서 원하는대로 설정
xdebug.idekey=VSCODE

xdebug.remote_autostart=1
xdebug.remote_enable=1
xdebug.cli_color=1
xdebug.profiler_enable=1
xdebug.profiler_output_dir="~/xdebug/phpstorm/tmp/profiling"

xdebug.remote_handler=dbgp
xdebug.remote_mode=req

xdebug.var_display_max_children=-1
xdebug.var_display_max_data=-1
xdebug.var_display_max_depth=-1
```

#### 3. docker-compose build --no-cache workspace php-fpm

#### 4. vscode - php debug extension 설치 및 설정

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "pathMappings": {
                "/var/www/[your project folder name]": "${workspaceRoot}"
            },
            "log": true,
            "port": [same xdebug.ini]
        },
        {
            "name": "Launch currently open script",
            "type": "php",
            "request": "launch",
            "program": "${file}",
            "cwd": "${fileDirname}",
            "port": 9000
        }
    ]
}
```

##### REFERENCES

- https://blog.scottchayaa.com/post/2018/10/16/vscode-phpunit-on-laradock/
