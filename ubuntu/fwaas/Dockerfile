FROM openstackloci/neutron:ubuntu

ENV PROJECT=neutron-fwaas
ARG WHEELS
ARG PROJECT_REPO=https://git.openstack.org/openstack/${PROJECT}
ARG PROJECT_REF=master
ARG OVERRIDE=override

ADD $OVERRIDE /

RUN set -x \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends git \
    && /opt/loci/clone_project.sh \
    && /opt/loci/pip_install.sh /tmp/${PROJECT} \
    && apt-get purge -y --auto-remove git \
    && rm -rf /tmp/* /root/.cache
