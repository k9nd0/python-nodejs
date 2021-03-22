FROM image-registry.openshift-image-registry.svc:5000/openshift/postgresql:12 AS postgresql

FROM image-registry.openshift-image-registry.svc:5000/openshift/python:3.6-ubi8

USER root

COPY --from=postgresql /usr/bin/psql /usr/bin/

COPY . /tmp/src

RUN dnf module reset -y nodejs && \
    dnf module enable -y nodejs:14 && \
    dnf module -y update nodejs:14

USER 1001

ENV NPM_CONFIG_PREFIX=/opt/app-root \
    PYTHONPATH=/opt/app-root/src

