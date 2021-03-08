
FROM registry.access.redhat.com/ubi8/ubi-minimal:latest

ARG RELEASE_VER=4.7
ARG INSTALL_DIR=/root/ocp-install

ENV PATH $PATH:$INSTALL_DIR

WORKDIR $INSTALL_DIR

RUN microdnf update && \
    microdnf install -y yum findutils && \
    mkdir -p $INSTALL_DIR

RUN yum install -y openssh openssh-clients

COPY openshift-install-powervs /usr/bin/openshift-install-powervs

RUN chmod +x /usr/bin/openshift-install-powervs && \
    /usr/bin/openshift-install-powervs setup

ENTRYPOINT ["/bin/bash", "/usr/bin/openshift-install-powervs"]
