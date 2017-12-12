FROM alpine:3.7

RUN apk --no-cache add wget \
  && mkdir /usr/lib/fr24/ \
  && cd /tmp \
  && wget http://feed.flightradar24.com/linux/fr24feed_1.0.18-5_amd64.tgz \
  && tar zxf /tmp/fr24feed_1.0.18-5_amd64.tgz \
  && cp fr24feed_amd64/fr24feed /usr/lib/fr24/ \
  && rm -rf *

COPY fr24feed.ini /etc/fr24feed.ini

WORKDIR /usr/lib/fr24/

EXPOSE 8754

ENTRYPOINT ["./fr24feed"]