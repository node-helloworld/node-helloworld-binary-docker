FROM bitnami/minideb-extras:stretch-r185
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.14.4-2 --checksum ad88cd21120c64e122feac5c0f5c33d7ceb85ecd78c5263baaaa95554a9b1d3d
RUN bitnami-pkg unpack canary-binary-1.0.15-1 --checksum a23654ec206c3e56420e84c7715765970d3f40836d6b1981f59f55b16e6fa69c

COPY rootfs /
ENV BITNAMI_APP_NAME="canary-binary" \
    BITNAMI_IMAGE_VERSION="1.0.15-debian-9-r24" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary-binary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary-binary" ]
