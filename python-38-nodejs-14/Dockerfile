FROM image-registry.openshift-image-registry.svc:5000/openshift/python:3.8-ubi8

USER root

RUN ls -l; pwd;

COPY . /tmp/src

RUN ls -l /tmp/src

RUN dnf install -y /tmp/src/packages/libicu-60.3-2.el8_1.x86_64.rpm /tmp/src/packages/postgresql-12.5-1.module+el8.3.0+9042+664538f4.x86_64.rpm

RUN dnf module reset -y nodejs && \
    dnf module enable -y nodejs:14 && \
    dnf module -y update nodejs:14

USER 1001

ENV NPM_CONFIG_PREFIX=/opt/app-root \
    PYTHONPATH=/opt/app-root/src

