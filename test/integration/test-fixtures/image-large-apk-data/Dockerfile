FROM alpine@sha256:b89d9c93e9ed3597455c90a0b88a8bbb5cb7188438f70953fede212a0c4394e0

# we keep these unpinned so that if alpine
# changes our integration tests can adapt
RUN apk add --no-cache \
            tzdata \
            vim \
            alpine-sdk
