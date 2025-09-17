FROM dhenyson/heavy-php:8.3-fpm-alpine-redis

RUN apk update && apk add --no-cache \
  supervisor \
  curl \
  wget \
  nginx \
  unzip \
  redis \
  git \
  php83-gd \
  php83-common \
  php83-fpm \
  php83-pdo \
  php83-opcache \
  php83-zip \
  php83-phar \
  php83-iconv \
  php83-cli \
  php83-curl \
  php83-openssl \
  php83-mbstring \
  php83-tokenizer \
  php83-fileinfo \
  php83-json \
  php83-xml \
  php83-xmlwriter \
  php83-xmlreader \
  php83-simplexml \
  php83-dom \
  php83-pdo_sqlite \
  php83-pdo_pgsql \
  php83-pecl-redis \
  php83-ctype \
  php83-sodium \
  php83-pcntl \
  php83-posix \
  # Libraries required at runtime for extensions
  libzip \
  freetype \
  libjpeg-turbo \
  libpng \
  libxml2 \
  libxslt \
  postgresql-libs \
  oniguruma \
  icu-libs \
  unixodbc \
  freetds && \
  # Install Microsoft ODBC Driver for SQL Server
  ARCH=$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/') && \
  curl -O https://download.microsoft.com/download/3/5/5/355d7943-a338-41a7-858d-53b259ea33f5/msodbcsql18_18.3.3.1-1_${ARCH}.apk && \
  curl -O https://download.microsoft.com/download/3/5/5/355d7943-a338-41a7-858d-53b259ea33f5/mssql-tools18_18.3.1.1-1_${ARCH}.apk && \
  apk add --allow-untrusted msodbcsql18_18.3.3.1-1_${ARCH}.apk && \
  apk add --allow-untrusted mssql-tools18_18.3.1.1-1_${ARCH}.apk && \
  rm msodbcsql18_18.3.3.1-1_${ARCH}.apk mssql-tools18_18.3.1.1-1_${ARCH}.apk && \
  # Build dependencies (will be removed)
  apk add --no-cache --virtual .build-deps \
  $PHPIZE_DEPS \
  gcc \
  g++ \
  make \
  autoconf \
  build-base \
  libmcrypt-dev \
  libzip-dev \
  freetype-dev \
  libjpeg-turbo-dev \
  libpng-dev \
  libxml2-dev \
  libxslt-dev \
  postgresql-dev \
  oniguruma-dev \
  icu-dev \
  unixodbc-dev \
  freetds-dev && \
  # Install and configure PHP extensions
  docker-php-ext-configure gd --with-freetype --with-jpeg && \
  docker-php-ext-install pdo pdo_mysql pdo_pgsql fileinfo gd xml xsl mbstring bcmath pcntl exif intl zip posix && \
  pecl install sqlsrv pdo_sqlsrv redis && \
  docker-php-ext-enable sqlsrv pdo_sqlsrv redis && \
  # Clean build dependencies and caches
  apk del .build-deps && \
  rm -rf /var/cache/apk/*

WORKDIR /app

ENTRYPOINT ["/app/docker/start-server.sh"]
