FROM registry.access.redhat.com/ubi7/ubi-minimal:latest

RUN rpm -e pinentry gnupg2 gpgme librepo libdnf microdnf pth \
           shared-mime-info glib2 json-glib gobject-introspection libpeas \
           librhsm pkgconfig libmodulemd libmount expat libsolv libyaml \
           libsmartcols json-c libgcrypt libxml2 libblkid libassuan libuuid \
           libgpg-error

ENV OPERATOR=/usr/local/bin/submariner-operator \
    USER_UID=1001 \
    USER_NAME=submariner-operator

# install operator binary
COPY build/_output/bin/submariner-operator ${OPERATOR}

COPY build/bin /usr/local/bin
RUN  /usr/local/bin/user_setup

ENTRYPOINT ["/usr/local/bin/entrypoint"]

USER ${USER_UID}
