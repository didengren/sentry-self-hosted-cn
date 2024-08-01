ARG BASE_IMAGE
FROM ${BASE_IMAGE}
USER 0

#更换debian的源
RUN if [ -f "/etc/apt/sources.list" ]; then sed -i s@/deb.debian.org/@/mirrors.aliyun.com/@g /etc/apt/sources.list; fi
RUN if [ -f "/etc/apt/sources.list.d/debian.sources" ]; then sed -i s@/deb.debian.org/@/mirrors.aliyun.com/@g /etc/apt/sources.list.d/debian.sources; fi

RUN if [ -n "${http_proxy}" ]; then echo "Acquire::http::proxy \"${http_proxy}\";" >> /etc/apt/apt.conf; fi
RUN if [ -n "${https_proxy}" ]; then echo "Acquire::https::proxy \"${https_proxy}\";" >> /etc/apt/apt.conf; fi
RUN apt-get update && apt-get install -y --no-install-recommends cron && \
    rm -r /var/lib/apt/lists/*
COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
