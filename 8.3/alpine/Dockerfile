FROM php:8.3-alpine

LABEL org.opencontainers.image.source="https://github.com/104lab/docker-octane" \
    repository="https://github.com/104lab/docker-octane"

# Set build deps
ENV BUILD_DEPS \
        libpq-dev \
        sqlite-dev

# See https://laravel.com/docs/11.x/deployment#server-requirements
# See https://pecl.php.net/package/openswoole
RUN set -xe && \
            apk add --no-cache \
                libpq \
                libstdc++ \
                sqlite \
                ${BUILD_DEPS} \
        && \
            docker-php-ext-install \
                pcntl \
                pdo_mysql \
                pdo_pgsql \
                pdo_sqlite \
        && \
            apk add --no-cache --virtual .build-deps \
                autoconf \
                g++ \
                make \
        && \
            pecl install \
                openswoole-22.1.2 \
        && \
            docker-php-ext-enable \
                openswoole \
        && \
            apk del .build-deps && \
            apk del ${BUILD_DEPS} && \
            php -m
