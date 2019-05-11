ARG arch=armhf
ARG arch_qemu=arm
FROM debian:stretch-slim AS qemu

RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get install -y --no-install-recommends qemu-user-static

FROM ${arch}/debian:stretch-slim

ARG arch_qemu

MAINTAINER Ignacio Núñez Hernanz <nacho@ownyourbits.com>

CMD /bin/bash

COPY --from=qemu /usr/bin/qemu-${arch_qemu}-static /usr/bin/

RUN mkdir -p /etc/services-available.d  /etc/services-enabled.d

COPY docker/debian-ncp/run-parts.sh /
