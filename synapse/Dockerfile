FROM alpine:3.7

ENV SYNAPSE_VERSION 0.25.1

RUN apk add --no-cache \
		ca-certificates \
		gcc \
		libffi-dev \
		libjpeg-turbo-dev \
		libressl-dev \
		libtool \
		libzip-dev \
		make \
		musl-dev \
		python2-dev \
		py-libxslt \
		py-twisted \
		py2-cffi \
		py2-dateutil \
		py2-decorator \
		py2-ipaddress \
		py2-msgpack \
		py2-netaddr \
		py2-pillow \
		py2-pip \
		py2-psutil \
		py2-psycopg2 \
		py2-setuptools \
		py2-simplejson \
		py2-six \
		py2-yaml \
	&& pip install "https://github.com/matrix-org/synapse/tarball/v$SYNAPSE_VERSION"

EXPOSE 8008
EXPOSE 8448
VOLUME /var/lib/synapse

WORKDIR /var/lib/synapse

# RUN /usr/bin/python2 -m synapse.app.homeserver \
# 		--server-name your.server.com \
# 		--config-path /etc/synapse/homeserver.yaml \
# 		--generate-config \
# 		--report-stats=no \
#  && rm /etc/synapse/homeserver.yaml

ADD files/homeserver.yaml /etc/synapse/homeserver.yaml

CMD /usr/bin/python2 -m synapse.app.homeserver \
		--config-path=/etc/synapse/homeserver.yaml
