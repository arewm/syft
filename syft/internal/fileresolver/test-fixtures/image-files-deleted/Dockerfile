FROM alpine:3.20.3@sha256:beefdbd8a1da6d2915566fde36db9db0b524eb737fc57cd1367effd16dc0d06d as tools
FROM scratch
COPY --from=tools /bin /bin
COPY --from=tools /lib /lib
ADD . .
RUN rm -rf file-1.txt /bin /lib
