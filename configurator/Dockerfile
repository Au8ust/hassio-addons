ARG BUILD_FROM
FROM $BUILD_FROM

# Add env
ENV LANG C.UTF-8

# Setup base
ARG CONFIGURATOR_VERSION
RUN apk add --no-cache python3 git curl \
  && pip3 install GitPython \
  && curl -s -o /configurator.py https://raw.githubusercontent.com/danielperna84/hass-configurator/$CONFIGURATOR_VERSION/configurator.py \
  && sed -i "s/GIT = False/GIT = True/g" /configurator.py \
  && apk del curl

# Copy data
COPY map.py run.sh /
RUN chmod a+x /run.sh

CMD ["/run.sh"]
