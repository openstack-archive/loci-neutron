FROM openstackloci/neutron:debian

ENV PROJECT=neutron-fwaas
ARG WHEELS
ARG PROJECT_REPO=https://git.openstack.org/openstack/${PROJECT}
ARG PROJECT_REF=master
ARG OVERRIDE=override

ADD $OVERRIDE /

RUN set -x \
    && yum upgrade -y \
    && yum install -y git \
    && /opt/loci/clone_project.sh \
    && /opt/loci/pip_install.sh /tmp/${PROJECT} \
    && yum -y autoremove git \
    && yum clean all
