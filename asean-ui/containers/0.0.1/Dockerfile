FROM nginx:1.13.3-alpine

COPY entry.sh /usr/bin/
COPY conf.d /etc/confd/conf.d
COPY templates /etc/confd/templates

RUN apt-get update \
 && apt-get upgrade -y \
 && apt-get install -y --no-install-recommends \
            curl \
            jq \
 && rm -rf /var/lib/apt/lists/* \
 && rm -rf /tmp/* /var/tmp/*

 RUN curl -L https://github.com/kelseyhightower/confd/releases/download/v0.11.0/confd-0.11.0-linux-amd64 -o /usr/local/bin/confd \
 && chmod +x /usr/local/bin/confd

ENTRYPOINT ["/usr/bin/entry.sh"]
