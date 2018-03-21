FROM nginx:1.9
MAINTAINER neo<neo@mailejifen.com>
ADD  ./nginx.conf      /etc/nginx/nginx.conf
ADD  ./fastcgi_params  /etc/nginx/fastcgi_params
#私有配置，配置你的vhosts
ADD  ./vhosts /etc/nginx/vhosts
RUN mkdir -p /www/ && mkdir -p /var/log/nginx/


