FROM alpine:3.8
MAINTAINER FAN VINGA<fanalcest@gmail.com>

ADD Caddyfile /Caddyfile
 
RUN apk --no-cache add curl git wget tar gzip bzip2 xz svn p7zip&& \
    curl "https://caddyserver.com/download/linux/amd64?plugins=http.filemanager&license=personal&telemetry=off" | tar -xz caddy && \    
    mkdir -p /fm  && \
    mv caddy /usr/bin/caddy && \
    chmod -R 777 /usr/bin/caddy

RUN ln -s /tmp /.caddy

USER fm
ENV USER=fm
    
WORKDIR /fm
EXPOSE 8080

CMD mkdir /fm/db && \
    mkdir /fm/share && \
    caddy -conf /Caddyfile
