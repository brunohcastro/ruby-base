FROM ruby:3-alpine

RUN apk update \
    && apk add --no-cache \
        ca-certificates \
        curl \
        tzdata \
        git \
        build-base \
        linux-headers \
        sqlite \
        sqlite-dev \
        # postgresql-client \
        # postgresql-dev \
        # mysql-client \
        # mysql-dev \
        coreutils

ENV BUNDLE_PATH=/bundle \
    BUNDLE_BIN=/bundle/bin \
    GEM_HOME=/bundle

ENV PATH="$BUNDLE_BIN:$PATH"

ARG USER_ID=1000
ARG GROUP_ID=1000

RUN addgroup -g ${GROUP_ID} app \
  && adduser -s /bin/ash -u ${USER_ID} -G app -h /home/app -S -D app \
  && mkdir /app && chown -R app:app /app \
  && mkdir /bundle \
  && chown -R app:app /bundle

USER app

WORKDIR /app