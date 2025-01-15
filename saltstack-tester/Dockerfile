ARG OSVERSION=24.04@sha256:80dd3c3b9c6cecb9f1667e9290b3bc61b78c2678c02cbdae5f0fea92cc6734ab

FROM ubuntu:$OSVERSION

ARG SALTVERSION=3006

ENV DEBIAN_FRONTEND=noninteractive

RUN \
    apt-get update && \
    apt-get install -y wget gnupg git && \
    wget -O - "https://packages.broadcom.com/artifactory/api/security/keypair/SaltProjectKey/public" | tee /etc/apt/keyrings/salt-archive-keyring.pgp && \
    wget -O - "https://github.com/saltstack/salt-install-guide/releases/latest/download/salt.sources" | tee /etc/apt/sources.list.d/salt.sources && \
    echo "Package: salt-*\nPin: version ${SALTVERSION}.*\nPin-Priority: 1001" | tee /etc/apt/preferences.d/salt-pin-1001 && \
    apt-get update && \
    apt-get install -y salt-common
