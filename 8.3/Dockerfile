FROM php:8.3

LABEL org.opencontainers.image.source="https://github.com/104lab/docker-octane" \
    repository="https://github.com/104lab/docker-octane"

# Set build deps
ENV BUILD_DEPS \
        libpq-dev \
        libsqlite3-dev

# See https://laravel.com/docs/11.x/deployment#server-requirements
# See https://pecl.php.net/package/openswoole
RUN set -xe && \
            apt-get update && \
            apt-get install --yes --no-install-recommends --no-install-suggests \
                libpq5 \
                ${BUILD_DEPS} \
        && \
            docker-php-ext-install \
                pcntl \
                pdo_mysql \
                pdo_pgsql \
                pdo_sqlite \
        && \
            pecl install \
                openswoole-22.1.2 \
        && \
            docker-php-ext-enable \
                openswoole \
        && \
            apt-get remove --purge -y ${BUILD_DEPS} && \
            apt-get autoremove --purge -y && \
            rm -r /var/lib/apt/lists/* && \
            php -m
