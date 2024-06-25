FROM debian:sid@sha256:51f59d258850c5ec72f775f11334ec2067c3df6b5a09f1e790eb418d837fb6ea
ADD sources.list /etc/apt/sources.list.d/sources.list
RUN apt update -y && apt install -y dpkg-dev
# this as a "macho-invalid" directory which is useful for testing
RUN apt-get source -y clang-13
