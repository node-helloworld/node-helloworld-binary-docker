FROM bitnami/minideb-extras:stretch-r208
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages ghostscript imagemagick libbz2-1.0 libc6 libgcc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 net-tools zlib1g
RUN bitnami-pkg install node-6.15.0-0 --checksum cee7bbc73f2a082113bb795e11f2b9f3fb13aca2feef0ae5ac4f96cd899c25b5
RUN bitnami-pkg unpack canary-binary-1.0.15-1 --checksum a23654ec206c3e56420e84c7715765970d3f40836d6b1981f59f55b16e6fa69c

COPY rootfs /
ENV BITNAMI_APP_NAME="canary-binary" \
    BITNAMI_IMAGE_VERSION="1.0.15-debian-9-r46" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/canary-binary/bin:$PATH"

EXPOSE 8080

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "canary-binary" ]
