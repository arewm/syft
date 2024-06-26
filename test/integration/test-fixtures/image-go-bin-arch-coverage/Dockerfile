FROM golang:1.21.1@sha256:19600fdcae402165dcdab18cb9649540bde6be7274dedb5d205b2f84029fe909 as builder
WORKDIR /app
COPY go.sum go.mod app.go ./

RUN GOOS=linux go build -o elf .
RUN GOOS=windows go build -o win .
RUN GOOS=darwin go build -o macos .

FROM scratch

WORKDIR /tmp
COPY --from=builder /app/elf /
COPY --from=builder /app/win /
COPY --from=builder /app/macos /

ENTRYPOINT ["/elf"]
