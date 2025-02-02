FROM nginx:alpine

RUN apk update && apk add --no-cache wget curl bash

RUN wget https://github.com/nginx/nginx-prometheus-exporter/releases/download/v1.4.1/nginx-prometheus-exporter_1.4.1_linux_amd64.tar.gz \
    && tar -xvzf nginx-prometheus-exporter_1.4.1_linux_amd64.tar.gz \
    && mv nginx-prometheus-exporter /usr/local/bin/

COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80 9113

CMD /usr/local/bin/nginx-prometheus-exporter -nginx.scrape-uri=http://localhost:80/stub_status & \
    nginx -g 'daemon off;'


