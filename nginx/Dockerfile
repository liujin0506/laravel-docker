FROM nginx:1.19.6-alpine

MAINTAINER liujing <liujing@addnewer.com>

#https://yeasy.gitbooks.io/docker_practice/content/image/build.html
RUN mkdir -p /etc/nginx/cert \
	&& mkdir -p /etc/nginx/conf.d

COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./enable-php.conf /etc/nginx/enable-php.conf
COPY ./conf.d/ /etc/nginx/conf.d/
COPY ./cert/ /etc/nginx/cert/

# mount nginx log
VOLUME /var/log/nginx

WORKDIR /data/www
