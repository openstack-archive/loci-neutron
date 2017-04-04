FROM ubuntu:xenial

ENV PROJECT=neutron
ARG DOCKER_REPO=yaodu/openstack-requirements
ARG DOCKER_TAG=ubuntu
ARG WHEELS
ARG PROJECT_REPO=https://git.openstack.org/openstack/${PROJECT}
ARG PROJECT_REF=master
ARG SCRIPTS_REPO=https://github.com/openstack/loci
ARG SCRIPTS_REF=master
ARG OVERRIDE=override

ADD $OVERRIDE /

RUN set -x \
    && apt-get update \
    && apt-get install -y --no-install-recommends python ca-certificates curl git \
    && git init /tmp/common/ \
    && git --git-dir /tmp/common/.git fetch --depth 1 $SCRIPTS_REPO $SCRIPTS_REF \
    && git --git-dir /tmp/common/.git/ checkout FETCH_HEAD  \
    && git --git-dir /tmp/common/.git fetch --depth 1 $SCRIPTS_REPO $SCRIPTS_REF \
    && git --git-dir /tmp/common/.git/ checkout FETCH_HEAD  \
    && /tmp/common/scripts/download.sh \
    && /tmp/common/scripts/install.sh \
    && apt-get install -y --no-install-recommends \
        bridge-utils \
        conntrack \
        dnsmasq \
        dnsmasq-utils \
        ebtables \
        iproute2 \
        ipset \
        iptables \
        iputils-arping \
        keepalived \
        openvswitch-switch \
        uuid-runtime \
    && /tmp/common/scripts/cleanup.sh
