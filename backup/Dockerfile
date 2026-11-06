ARG UBUNTU_VERSION=26.04
FROM --platform=linux/arm64 ubuntu:${UBUNTU_VERSION}

WORKDIR /app
COPY backup .
RUN chmod +x backup

ENTRYPOINT ["./backup"]
CMD ["list"]
