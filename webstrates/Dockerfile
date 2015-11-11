FROM dockerfile/ubuntu
MAINTAINER 3846masa <3846masahiro+git@gmail.com>

RUN apt update && \
    apt install -y curl && \
    curl -sL https://deb.nodesource.com/setup | bash -

RUN apt update && \
    apt install -y mongodb git nodejs python build-essential && \
    mkdir -p /data/db

RUN git clone https://github.com/cklokmose/Webstrates.git ~/Webstrates

RUN cd ~/Webstrates && \
    npm set strict-ssl false && \
    npm install -g coffee-script && \
    npm install && \
    cake build

ADD start.sh /root/Webstrates/start.sh

EXPOSE 7007

VOLUME ["/data/db"]

WORKDIR "/root/Webstrates"

CMD ["bash", "/root/Webstrates/start.sh"]
