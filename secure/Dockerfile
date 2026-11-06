FROM ubuntu:24.04

RUN apt-get update && apt-get install -y nginx && rm -rf /var/lib/apt/lists/*

# create non-root user
RUN useradd --create-home appuser

# Configure nginx to listen on port 8080
# non-root user cannot listen to port 80
RUN sed -i 's/listen 80;/listen 8080;/' /etc/nginx/sites-enabled/default

# switch to non-root user
USER appuser

CMD ["nginx", "-g", "daemon off;"]

