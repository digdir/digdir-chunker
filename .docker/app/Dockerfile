# filepath: ./Dockerfile
FROM jkaninda/laravel-php-fpm:latest@sha256:9f5ba756b4c90165a9a87d0e1086554a7d554ee56cd06ac54c050257905f9f56

ENV PATH="/opt/marker/bin:${PATH}"

RUN apt update \
    && apt install -y poppler-utils \
    && apt install -y python3-pip python3-venv \
    && python3 -m venv /opt/marker \
    && /opt/marker/bin/pip install --upgrade pip \
    && /opt/marker/bin/pip install 'marker-pdf[full]' \
    && apt clean

RUN chown -R www-data:www-data /opt/marker

# Set the working directory
WORKDIR /var/www/html

COPY .docker/app/entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]