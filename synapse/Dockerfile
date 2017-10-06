FROM alpine:3.6

ENV SYNAPSE_VERSION 0.23.1

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

ADD files/homeserver.yaml /etc/synapse/homeserver.yaml

# stack.so workaround for Python's ujson bug
# https://github.com/esnme/ultrajson/issues/254#issuecomment-314862445
CMD LD_PRELOAD=/etc/synapse/conf/stack.so /usr/bin/python2 -m synapse.app.homeserver \
		--config-path=/etc/synapse/homeserver.yaml
