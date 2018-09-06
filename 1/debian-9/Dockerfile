FROM bitnami/minideb-extras:stretch-r130
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.14.4-0 --checksum 0c3fabdfd28a431e807fde7e1d10a9e09a6d12b5e7b0f69b339bd4a606310881
RUN bitnami-pkg unpack canary-binary-1.0.14-0 --checksum 995165f071dc4be39eb16b888d384732821b4eff03251abf2296277c7a8f142d

COPY rootfs /
ENV BITNAMI_APP_NAME="canary-binary" \
    BITNAMI_IMAGE_VERSION="1.0.14-debian-9-r26" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary-binary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary-binary" ]