FROM alpine:3.7

LABEL org.opencontainers.image.source="https://github.com/the2hill/encore-webhook-receiver"
LABEL maintainer="Phillip Toohill <phillip.toohill@rackspace.com>"

ENV env_workspace_directory=$workspace_directory

COPY . ${env_workspace_directory}

RUN cd ${env_workspace_directory}

RUN apk update \
    && apk add py-pip bash gcc python-dev musl-dev libffi-dev openssl-dev unzip \
    && rm -rf /var/cache/apk/* \
    && pip install -r requirements.txt \
    && chmod +x docker/run.sh

EXPOSE 9119

ENTRYPOINT ["./run.sh"]