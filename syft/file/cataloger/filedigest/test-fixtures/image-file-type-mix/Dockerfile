FROM busybox:1.36.1@sha256:c230832bd3b0be59a6c47ed64294f9ce71e91b327957920b6929a0caa8353140

ADD file-1.txt .
RUN chmod 644 file-1.txt
RUN chown 1:2 file-1.txt
RUN ln -s file-1.txt symlink-1
# note: hard links may behave inconsistently, this should be a golden image
RUN ln file-1.txt hardlink-1
RUN mknod char-device-1 c 89 1
RUN mknod block-device-1 b 0 1
RUN mknod fifo-1 p
RUN mkdir /dir
RUN rm -rf home etc/group etc/localtime etc/mtab etc/network etc/passwd etc/shadow var usr bin/*