FROM alpine:latest

LABEL maintainer="Agha Reza"

ENV TIMEZONE Asia/Tehran

RUN     apk update && \
        apk upgrade && \
        apk add --update nginx && \
        apk add --update tzdata && \
        cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && \
        echo "${TIMEZONE}" > /etc/timezone && \
	    mkdir /www && \
	    apk del tzdata && \
	    rm -rf /var/cache/apk/*

COPY etc/default.conf /etc/nginx/http.d/default.conf

VOLUME ["/etc/nginx/conf.d", "/etc/nginx/http.d", "/var/log/nginx", "/www"]

EXPOSE 80

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"] 