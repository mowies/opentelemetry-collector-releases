FROM ghcr.io/linuxcontainers/alpine:3.20 as certs
RUN apk --update add ca-certificates

FROM scratch

ARG SERVICE_NAME=ocb
ARG USER_UID=10001
ARG USER_GID=10001
USER ${USER_UID}:${USER_GID}

USER ${SERVICE_NAME}
WORKDIR /home/${SERVICE_NAME}

COPY --from=certs /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt
COPY --chmod=755 ocb /usr/local/bin/ocb
ENTRYPOINT [ "ocb" ]
