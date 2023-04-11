FROM alpine:3.17

LABEL maintainer="QiuDog <qiudog825@gmail.com>"

ARG TZ='Asia/Shanghai'
ARG ARCH
ARG KCP_VERSION

ENV ARCH ${ARCH}
ENV TZ ${TZ}
ENV KCP_VERSION ${KCP_VERSION}
ENV KCP_DOWNLOAD_URL https://github.com/xtaci/kcptun/releases/download/v${KCP_VERSION}/kcptun-linux-${ARCH}-${KCP_VERSION}.tar.gz

RUN apk update \
    && apk add --no-cache bash tzdata curl \
    && curl -sSLO ${KCP_DOWNLOAD_URL} \
    && tar -zxf kcptun-linux-${ARCH}-${KCP_VERSION}.tar.gz \
    && mv server_linux_${ARCH} /usr/bin/kcpserver \
    && mv client_linux_${ARCH} /usr/bin/kcpclient \
    && rm -rf kcptun-linux-${ARCH}-${KCP_VERSION}.tar.gz \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && apk del curl \
    && rm -rf /var/cache/apk/*

SHELL [ "/bin/bash", "-c" ]
