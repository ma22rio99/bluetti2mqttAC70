ARG BUILD_FROM
FROM $BUILD_FROM

RUN apk update && apk upgrade

# Copy data for add-on
COPY rootfs /
#install git
RUN apk add --no-cache git \
    && pip install git+https://github.com/bxm6306/bluetti_mqtt.git@patch-2 \
    && apk add --update --no-cache bluez=5.65-r0 \
    && rm -rf /var/cache/apk/* /lib/apk/db/* \
    && chmod a+x /run.sh


# Install bluetti_mqtt
RUN pip install git+https://github.com/bxm6306/bluetti_mqtt.git@patch-2 \
	&& apk add --update --no-cache \
		bluez=5.65-r0 \
	&& rm -rf /var/cache/apk/* /lib/apk/db/* \
	&& chmod a+x /run.sh

CMD [ "/run.sh" ]
