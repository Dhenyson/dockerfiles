# Build
heavy-php:8.3-fpm-alpine-redis:
```bash
cd repositories/heavy-php/tags/heavy-php:8.3-fpm-alpine-redis && \
docker build --no-cache -t dhenyson/heavy-php:8.3-fpm-alpine-redis .
```

heavy-php:8.3-fpm-alpine-redis-jdk8:
```bash
cd repositories/heavy-php/tags/heavy-php:8.3-fpm-alpine-redis-jdk8 && \
docker build --no-cache -t dhenyson/heavy-php:8.3-fpm-alpine-redis-jdk8 .
```

# Push
heavy-php:8.3-fpm-alpine-redis:
```bash
docker push dhenyson/heavy-php:8.3-fpm-alpine-redis
```

heavy-php:8.3-fpm-alpine-redis-jdk8:
```bash
docker push dhenyson/heavy-php:8.3-fpm-alpine-redis-jdk8
```