FROM dunglas/frankenphp:php8.4

RUN install-php-extensions \
    pdo_pgsql \
    intl \
    opcache

WORKDIR /app

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

COPY . .

RUN composer install --no-interaction --prefer-dist

COPY Caddyfile /etc/caddy/Caddyfile

CMD ["frankenphp", "run", "--config", "/etc/caddy/Caddyfile"]
