FROM fedora:41@sha256:be4799339fa9f6e733c135237b3ff598f69f57ab71460ad79be0d8f21b1aed2a

RUN dnf install 'dnf-command(download)' cpio xz -y
# https://dl.fedoraproject.org/pub/fedora/linux/releases/37/Everything/x86_64/os/Packages/k/kernel-6.0.7-301.fc37.x86_64.rpm
# https://dl.fedoraproject.org/pub/fedora/linux/releases/37/Everything/x86_64/os/Packages/k/kernel-modules-6.0.7-301.fc37.x86_64.rpm
RUN dnf download kernel-core-6.0.7-301.fc37 kernel-modules-6.0.7-301.fc37 -y

RUN rpm2cpio kernel-core-*.rpm | cpio -t && \
    rpm2cpio kernel-core-*.rpm | cpio -idmv ./lib/modules/6.0.7-301.fc37.x86_64/vmlinuz

RUN rpm2cpio kernel-modules-*.rpm | cpio -t && \
    rpm2cpio kernel-modules-*.rpm | cpio -idmv ./lib/modules/6.0.7-301.fc37.x86_64/kernel/drivers/tty/ttynull.ko.xz

RUN unxz /lib/modules/6.0.7-301.fc37.x86_64/kernel/drivers/tty/ttynull.ko.xz

FROM scratch

COPY --from=0 /lib/modules/6.0.7-301.fc37.x86_64/vmlinuz /lib/modules/6.0.7-301.fc37.x86_64/vmlinuz
COPY --from=0 /lib/modules/6.0.7-301.fc37.x86_64/kernel/drivers/tty/ttynull.ko /lib/modules/6.0.7-301.fc37.x86_64/kernel/drivers/tty/ttynull.ko
