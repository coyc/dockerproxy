FROM nginx:1.25.4

RUN rm -f /etc/nginx/conf.d/*

COPY .htpasswd /home
COPY conf.d/ /etc/nginx/conf.d/
COPY snippets/ /etc/nginx/snippets/
COPY sslkey.conf /home

WORKDIR /home

RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout sslkey.key -out sslkey.crt -config sslkey.conf \
    && mv sslkey.crt /etc/ssl/certs/sslkey.crt \
    && mv sslkey.key /etc/ssl/private/sslkey.key
