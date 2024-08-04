ARG BASE_IMAGE
FROM ${BASE_IMAGE}
USER 0

RUN if [ -n "${http_proxy}" ]; then echo "Acquire::http::proxy \"${http_proxy}\";" >> /etc/apt/apt.conf; fi
RUN if [ -n "${https_proxy}" ]; then echo "Acquire::https::proxy \"${https_proxy}\";" >> /etc/apt/apt.conf; fi

# 增加修改国内阿里debian源的步骤
RUN echo "deb http://mirrors.aliyun.com/debian  stable main contrib non-free" > /etc/apt/sources.list  \
    && echo "deb http://mirrors.aliyun.com/debian  stable-updates main contrib non-free" >> /etc/apt/sources.list  \
  && echo "deb https://mirrors.aliyun.com/debian/ bookworm main non-free non-free-firmware contrib" >> /etc/apt/sources.list  \
  && echo "deb-src https://mirrors.aliyun.com/debian/ bookworm main non-free non-free-firmware contrib" >> /etc/apt/sources.list  \
  && echo "deb https://mirrors.aliyun.com/debian-security/ bookworm-security main" >> /etc/apt/sources.list  \
  && echo "deb-src https://mirrors.aliyun.com/debian-security/ bookworm-security main" >> /etc/apt/sources.list  \
  && echo "deb https://mirrors.aliyun.com/debian/ bookworm-updates main non-free non-free-firmware contrib" >> /etc/apt/sources.list  \
  && echo "deb-src https://mirrors.aliyun.com/debian/ bookworm-updates main non-free non-free-firmware contrib" >> /etc/apt/sources.list  \
  && echo "deb https://mirrors.aliyun.com/debian/ bookworm-backports main non-free non-free-firmware contrib" >> /etc/apt/sources.list  \
  && echo "deb-src https://mirrors.aliyun.com/debian/ bookworm-backports main non-free non-free-firmware contrib" >> /etc/apt/sources.list  \
    && apt-get update && apt-get install -y --no-install-recommends cron && \
    rm -r /var/lib/apt/lists/*
COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
