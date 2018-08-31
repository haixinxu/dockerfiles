FROM golang as builder
RUN go get github.com/Lafeng/ezgoo && \
    cd /go/src/github.com/Lafeng/* && \
    go build --ldflags '-linkmode external -extldflags "-static"'

FROM alpine:3.8 
COPY --from=builder /go/src/github.com/Lafeng/*/ezgoo /app/
COPY dist /app/dist
RUN apk --no-cache add ca-certificates
RUN chmod +x /app/ezgoo

WORKDIR /app
EXPOSE 8080

USER ezgoo
ENV USER=ezgoo

CMD cp -r /app/dist /tmp/dist && \
    /app/ezgoo -dir=/tmp/dist 
