FROM dhenyson/heavy-php:8.3-fpm-alpine-redis

RUN apk update && apk add --no-cache \
  openjdk8 \
  openjdk8-jre

ENTRYPOINT ["/app/docker/start-server.sh"]