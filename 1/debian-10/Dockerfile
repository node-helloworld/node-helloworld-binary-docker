FROM bitnami/minideb:buster
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV PATH="/opt/bitnami/node/bin:/opt/bitnami/canary-binary/bin:/opt/bitnami/nami/bin:$PATH"

COPY prebuildfs /
# Install required system packages and dependencies
RUN install_packages ca-certificates curl dirmngr ghostscript gnupg imagemagick libbz2-1.0 libc6 libgcc1 libncursesw6 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo6 net-tools procps sudo unzip zlib1g
RUN /build/bitnami-user.sh && \
    /build/install-nami.sh
RUN bitnami-pkg install node-12.16.0-0 --checksum b274be80aad7d2da5984be9e0038ae3b2cd9d6830eae3f20d77c6ac8bf2275db
RUN bitnami-pkg unpack canary-binary-1.1.1-0 --checksum 93a0bd84a8b8b3652d06b4dd4e7179844b7fd25358c01398e94d2069222540d2
RUN apt-get update && apt-get upgrade && \
    rm -r /var/lib/apt/lists /var/cache/apt/archives
RUN /build/install-gosu.sh
RUN /build/install-tini.sh

COPY rootfs /
ENV BITNAMI_APP_NAME="canary-binary" \
    BITNAMI_IMAGE_VERSION="1.1.1-debian-10-r16"

EXPOSE 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary-binary" ]
