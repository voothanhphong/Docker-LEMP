FROM alpine

MAINTAINER VooThanh DEV <voothanhphong@gmail.com>

COPY entrypoint /
COPY include/default.vcl /etc/varnish/default.vcl

RUN apk add --update varnish && \
    sed -i -e 's/\r$//' /entrypoint && \
    chmod +x /entrypoint && \
    rm -rf /var/cache/apk/*

WORKDIR /etc/varnish

EXPOSE 6081 6082

CMD ["/entrypoint"]