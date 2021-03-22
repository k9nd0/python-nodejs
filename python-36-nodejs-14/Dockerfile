FROM image-registry.openshift-image-registry.svc:5000/openshift/python:3.6-ubi8

USER root

RUN git clone https://github.com/k9nd0/python-nodejs.git && \
    dnf install -y python-nodejs/packages/libicu-60.3-2.el8_1.x86_64.rpm python-nodejs/packages/postgresql-12.5-1.module+el8.3.0+9042+664538f4.x86_64.rpm && \
    rm -rf python-nodejs

RUN dnf module reset -y nodejs && \
    dnf module enable -y nodejs:14 && \
    dnf module -y update nodejs:14

USER 1001

ENV NPM_CONFIG_PREFIX=/opt/app-root \
    PYTHONPATH=/opt/app-root/src

