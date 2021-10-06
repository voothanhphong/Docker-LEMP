FROM nginx:alpine

MAINTAINER VooThanh DEV <voothanhphong@gmail.com>

ENV SERVER_NAME local.io
ENV IS_MAGENTO false
ENV VARNISH ""
ENV ROOT_FOLDER /project

COPY vhost/ /etc/nginx/vhost/
COPY include/ /etc/nginx/include/
COPY config/*.conf /etc/nginx/conf.d/
COPY bin/* /usr/local/bin/
COPY entrypoint /

RUN apk update && \
    apk add bash && \
    apk add openssl
RUN addgroup -g 1000 www \
    && adduser -G www -D -u 1000 -s /bin/bash www \
    && touch /var/run/nginx.pid \
    && mkdir -p ${ROOT_FOLDER} /sock \
    && mv -f /etc/nginx/include/nginx.conf /etc/nginx/nginx.conf \
    && chown -R www:www /etc/nginx /var/cache/nginx /var/run/nginx.pid /var/log/nginx \
    && chown -R www:www "${ROOT_FOLDER}" /sock /entrypoint \
    && chmod +x /entrypoint \
    && chmod +x /usr/local/bin/*
RUN rm -rf /var/cache/apk/*

WORKDIR ${ROOT_FOLDER}

ENTRYPOINT ["/entrypoint"]

EXPOSE 443 80

USER www

CMD ["nginx", "-g", "daemon off;"]