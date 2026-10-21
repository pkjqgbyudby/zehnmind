FROM alpine:3.20 AS builder
WORKDIR /build
COPY index.html .
RUN sed -i "s/__BUILD_DATE__/$(date -u +%Y-%m-%dT%H:%M:%SZ)/" index.html

FROM nginx:1.27-alpine
COPY --from=builder /build/index.html /usr/share/nginx/html/index.html
EXPOSE 80