FROM nginx:latest

LABEL maintainer admin@diendannhatban.info

RUN apt-get update && apt-get install -y \
        wget && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ADD https://dl.eff.org/certbot-auto /usr/local/bin/certbot-auto
RUN chmod a+x /usr/local/bin/certbot-auto
RUN certbot-auto --os-packages-only -n

WORKDIR /root/ddnb

EXPOSE 80
EXPOSE 443

COPY docker/build/nginx/entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh
# ENTRYPOINT ["entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]

RUN nginx -V
RUN certbot-auto --version