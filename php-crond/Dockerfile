FROM liujin0506/alpine-php7:latest

MAINTAINER liujing <liujing@addnewer.com>

COPY ./crontabs/default /var/spool/cron/crontabs/

RUN cat /var/spool/cron/crontabs/default >> /var/spool/cron/crontabs/root

WORKDIR /var/spool/cron/crontabs

RUN mkdir -p /var/log/cron \
	&& touch /var/log/cron/cron.log

VOLUME /var/log/cron

CMD ["/usr/sbin/crond", "-f", "-L", "/var/log/cron/cron.log"]
