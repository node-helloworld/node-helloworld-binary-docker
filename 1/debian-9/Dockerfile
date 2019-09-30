FROM bitnami/minideb-extras:stretch-r489
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.17.1-2 --checksum 21a8da5420ba31ad9b00bbc032f8456e114b857c45f63db47994f78f2d9d784a
RUN bitnami-pkg unpack canary-binary-1.0.15-21 --checksum 78c0fdeb6257a4fa20c964393803984e62b288f9ec1d4c6ed803966e9f17f4ef

COPY rootfs /
ENV BITNAMI_APP_NAME="canary-binary" \
    BITNAMI_IMAGE_VERSION="1.0.15-debian-9-r329" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary-binary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary-binary" ]
