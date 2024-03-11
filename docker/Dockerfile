FROM alpine:latest

WORKDIR /var/srv

RUN apk add jekyll
COPY serve.sh /serve.sh
COPY build.sh /build.sh

CMD /serve.sh
