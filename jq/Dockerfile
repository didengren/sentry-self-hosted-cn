FROM debian:bookworm-slim

LABEL MAINTAINER="oss@sentry.io"

#更换debian的源
RUN set -x \
  && echo "deb http://mirrors.aliyun.com/debian  stable main contrib non-free" > /etc/apt/sources.list  \
  && echo "deb http://mirrors.aliyun.com/debian  stable-updates main contrib non-free" >> /etc/apt/sources.list  \
  && apt-get update -y \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends jq \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["jq"]
