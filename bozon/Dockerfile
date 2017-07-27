FROM marthym/base:1.2.0
MAINTAINER marthym@github.com

RUN export DEBIAN_FRONTEND=noninteractive && \
    apt update && \
    apt install -y --no-install-recommends ca-certificates nginx php php-common php-cli php-fpm unzip && \
    wget https://github.com/broncowdd/BoZoN/archive/master.zip -O bozon.zip && \
    unzip bozon.zip && \
    mv BoZoN-master/ /var/www/bozon && \
    rm bozon.zip && \
    sed -i \
        -e 's|.*date.timezone.*|    if(!ini_get(\x27date.timezone\x27) ){date_default_timezone_set(\x27Europe/Paris\x27);}|g' \
        -e 's|.*cron_security_string.*| $cron_security_string=file_get_contents(\x27/bozon/cron_credentials\x27);if($cron_security_string===FALSE){throw new Exception(\x27Unable to load cron credentials\x27);}|g' \
        /var/www/bozon/config.php && \
    chown -R www-data:www-data /var/www/bozon && \
    ln -s /bozon/thumbs/ /var/www/bozon/thumbs && \
    ln -s /bozon/uploads/ /var/www/bozon/uploads && \
    ln -s /bozon/private/ /var/www/bozon/private && \
    apt purge -y wget libidn11 unzip && \
    apt autoremove && \
    apt clean && \
    rm -rf /var/lib/apt/lists/*

ADD etc/ /

RUN chmod +x /etc/sv/nginx/run && \
    ln -s /etc/nginx/sites-available/bozon.conf /etc/nginx/sites-enabled/bozon.conf && \
    rm -rf /etc/nginx/sites-enabled/default