FROM alpine:3.8

MAINTAINER sunchao

ENV GO_VERSION 1.11
ENV GOPATH /go

COPY source/go1.11.linux-amd64.tar.gz /tmp

RUN apk add --no-cache --virtual .build-deps  \
                ca-certificates \
                bash \
                gcc \
                musl-dev \
                go; \
    export GOROOT_BOOTSTRAP="$(go env GOROOT)"; \
    export GOOS="$(go env GOOS)"; \
    export GOHOSTOS="$(go env GOHOSTOS)"; \
    export GOHOSTARCH="$(go env GOHOSTARCH)"; \
    #make build
    tar -zxvf /tmp/go1.11.linux-amd64.tar.gz -C /usr/local; \
    rm /tmp/go1.11.linux-amd64.tar.gz; \
    cd /usr/local/go/src; \
    ./make.bash; \
    export PATH="/usr/local/go/bin:$PATH"; \
    mkdir -p "$GOPATH/src" "$GOPATH/bin" ; \
    chmod -R 777 "$GOPATH"; \
    go version;

ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

WORKDIR $GOPATH







