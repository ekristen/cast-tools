ARG OSVERSION=24.04@sha256:224a1869083a311ef3f13648a154ba79832fbef6364d31493642ca03082da254

FROM ubuntu:$OSVERSION

ARG SALTVERSION=3006

ENV DEBIAN_FRONTEND=noninteractive

RUN \
    apt-get update && \
    apt-get install -y wget gnupg git && \
    mkdir -p /etc/apt/keyrings && \
    wget -O - "https://packages.broadcom.com/artifactory/api/security/keypair/SaltProjectKey/public" | gpg --dearmor -o /etc/apt/keyrings/salt-archive-keyring.pgp && \
    wget -O - "https://github.com/saltstack/salt-install-guide/releases/latest/download/salt.sources" | tee /etc/apt/sources.list.d/salt.sources && \
    echo "Package: salt-*\nPin: version ${SALTVERSION}.*\nPin-Priority: 1001" | tee /etc/apt/preferences.d/salt-pin-1001 && \
    apt-get update && \
    apt-get install -y salt-common
