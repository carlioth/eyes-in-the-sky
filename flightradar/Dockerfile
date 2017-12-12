FROM alpine:3.7

RUN apk add -U gpgme
RUN gpg --keyserver pgp.mit.edu --recv-keys 40C430F5 && \
    gpg --armor --export 40C430F5 | apt-key add -

# Add APT repository to the config file, removing older entries if exist
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak && \
    grep -v flightradar24 /etc/apt/sources.list.bak > /etc/apt/sources.list && \
    echo 'deb http://repo.feed.flightradar24.com flightradar24 raspberrypi-stable' >> /etc/apt/sources.list

RUN apt-get update -y && apt-get install fr24feed -y

COPY fr24feed.ini /etc/fr24feed.ini

EXPOSE 8754

ENTRYPOINT ["/usr/bin/fr24feed"]