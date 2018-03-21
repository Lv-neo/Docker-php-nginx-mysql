# 使用说明

* docker 开发环境

```
php7 + nginx + mysql 
```

## 目录结构

```
├── docker-compose.yml
├── mysql
│   └── Dockerfile
├── nginx
│   ├── Dockerfile
│   ├── fastcgi_params
│   ├── index.html
│   ├── index.php
│   ├── nginx.conf
│   └── vhosts
├── php7
│   ├── composer.phar
│   ├── Dockerfile
│   ├── ext
│   │   ├── mongodb-1.2.9.tgz
│   │   ├── package.xml
│   │   ├── redis-3.1.2.tgz
│   │   ├── xdebug-2.5.3.tgz
│   │   └── yaconf-1.0.5.tgz
│   ├── php-fpm.conf
│   ├── php.ini
└── README.md
```

## 常用命令

## 更新与维护

