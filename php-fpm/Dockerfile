FROM liujin0506/alpine-php7:latest

MAINTAINER liujing <liujing@addnewer.com>

# https://pkgs.alpinelinux.org/packages

# Mirror mirror switch to Ali-OSM (Alibaba Open Source Mirror Site) - http://mirrors.aliyun.com/
RUN echo 'http://mirrors.aliyun.com/alpine/latest-stable/main' > /etc/apk/repositories \
	&& echo '@community http://mirrors.aliyun.com/alpine/latest-stable/community' >> /etc/apk/repositories \
	&& echo '@testing http://mirrors.aliyun.com/alpine/edge/testing' >> /etc/apk/repositories

# ensure www user exists
RUN set -x \
	&& addgroup -g 82 -S www \
	&& adduser -u 82 -D -S -G www www

# Mirror mirror switch to Alpine Linux - http://dl-4.alpinelinux.org/alpine/
RUN apk update \
	&& apk upgrade \
	&& apk add \
		tzdata \
	    php7-fpm@community \
	&& cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \
	&& echo "${TIMEZONE}" > /etc/timezone \
	&& apk del tzdata \
 	&& rm -rf /var/cache/apk/*

RUN mkdir -p /usr/share/nginx/html \
	&& mkdir -p /usr/local/var/log/php7 \
	&& mkdir -p /usr/local/var/log/php7 \
	&& mkdir -p /usr/local/var/run \
	&& mkdir -p /data/www

COPY ./php-fpm.conf /etc/php7/

COPY ./www.conf /etc/php7/php-fpm.d/

# Expose volumes
VOLUME ["/usr/share/nginx/html", "/usr/local/var/log/php7", "/var/run/", "/data/www"]

WORKDIR /data/www

EXPOSE 9000

CMD ["/usr/sbin/php-fpm7", "-R", "--nodaemonize"]
