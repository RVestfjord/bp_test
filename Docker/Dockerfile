FROM library/alpine:latest

RUN apk add -U nginx && mkdir /run/nginx
ADD nginx.conf /etc/nginx/nginx.conf

RUN mkdir -p /var/www/static
ADD index.html /var/www/static/index.html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
