FROM wordpress:php8.2-fpm

RUN pecl install xdebug

# Copy xdebug.ini to /usr/local/etc/php/conf.d/
COPY Wordpress/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

# Since this Dockerfile extends the official Docker image `wordpress`,
# and since `wordpress`, in turn, extends the official Docker image `php`,
# the helper script docker-php-ext-enable (defined for image `php`)
# works here, and we can use it to enable xdebug:
RUN docker-php-ext-enable xdebug && \
apt update && \
apt install zsh wget git fzf -y && \
usermod -s /usr/bin/zsh root && \
sh -c "$(wget -O- https://github.com/deluan/zsh-in-docker/releases/download/v1.1.5/zsh-in-docker.sh)" -- \
-p 'z' \
-p 'https://github.com/zsh-users/zsh-autosuggestions' \
-p 'https://github.com/zsh-users/zsh-syntax-highlighting' \
-a "bindkey '^I' autosuggest-accept" \
-a "zstyle ':bracketed-paste-magic' active-widgets '.self-*'"
