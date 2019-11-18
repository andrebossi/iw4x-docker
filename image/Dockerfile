FROM alpine:3

LABEL maintainer="andreluizbossi70@gmail.com" \
    description="Alpine based Wine environment for IW4x dedicated server."

ENV LANG en_US.utf8 \
    WINEARCH win32

RUN echo "x86" > /etc/apk/arch \
    && apk add --no-cache wine \
    && echo "x86_64" > /etc/apk/arch \
    && addgroup iw4x \
    && adduser -h "/iw4x" -G iw4x -D iw4x \
    && mkdir /iw4x/server

USER iw4x
WORKDIR /iw4x

COPY ./init.sh /iw4x/init.sh

VOLUME ["/iw4x/server"]

EXPOSE 28960 28960/udp

CMD ["/bin/sh", "-e", "init.sh"]