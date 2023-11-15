FROM    debian:bullseye

RUN		apt-get update
RUN		apt-get install -y nginx openssl

RUN mkdir /etc/nginx/ssl
RUN openssl req -newkey rsa:4096 -x509 -sha256 -days 365 -nodes \
       -out /etc/nginx/ssl/aelsiddi.crt \
       -keyout /etc/nginx/ssl/aelsiddi.key \
       -subj "/C=AE/ST=AD/L=AbuDhabi/O=42AD/CN=aelsiddi/"

COPY ./requirements/nginx/conf/nginx.conf /etc/nginx/conf.d

RUN mkdir -p /run/nginx && \
    chown -R www-data:www-data /var/www/html/

EXPOSE	443

CMD ["nginx", "-g", "daemon off;"]