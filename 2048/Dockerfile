FROM alpine:3.8
MAINTAINER FAN VINGA<fanalcest@gmail.com>

RUN apk --no-cache add nginx git && \
    git clone https://github.com/gabrielecirulli/2048 --depth 1 /app && \
    apk del git && rm -rf /app/.git

COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 8080

CMD nginx -g "daemon off;"
