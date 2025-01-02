FROM golang:1.23-alpine AS build

# renovate: datasource=go packageName=github.com/pdf/zfs_exporter/v2
ARG ZFS_EXPORTER_VERSION=v2.3.4

RUN apk add git && go install github.com/pdf/zfs_exporter/v2@${ZFS_EXPORTER_VERSION}

FROM alpine:3.21

RUN apk add zfs

COPY --from=build /go/bin/zfs_exporter /bin/

EXPOSE 9134

ENTRYPOINT [ "/bin/zfs_exporter" ]
