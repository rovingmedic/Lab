# stage 1: generate HTML
FROM ubuntu:24.04 AS builder

WORKDIR /build
COPY generate-status .
RUN chmod +x generate-status && ./generate-status > index.html

# stage 2: serve with nginx (unprivileged)
FROM nginxinc/nginx-unprivileged:1.28

# Labels
LABEL org.opencontainers.image.source="https://github.com/rovingmedic/Lab"
LABEL org.opencontainers.image.version="1.0.0"

# Copy generated HTML
COPY --from=builder /build/index.html /usr/share/nginx/html/index.html

# document port (unprivileged nginx uses 8080)
EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
	CMD curl -f http://localhost:8080/ || exit 1

