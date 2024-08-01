FROM debian:bookworm-slim

LABEL MAINTAINER="oss@sentry.io"

#更换debian的源
RUN if [ -f "/etc/apt/sources.list" ]; then sed -i s@/deb.debian.org/@/mirrors.aliyun.com/@g /etc/apt/sources.list; fi
RUN if [ -f "/etc/apt/sources.list.d/debian.sources" ]; then sed -i s@/deb.debian.org/@/mirrors.aliyun.com/@g /etc/apt/sources.list.d/debian.sources; fi

RUN set -x \
  && apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends jq \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["jq"]
