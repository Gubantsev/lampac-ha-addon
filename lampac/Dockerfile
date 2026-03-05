ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base:3.19
FROM ${BUILD_FROM}

ENV DOTNET_RUNNING_IN_CONTAINER=true \
    ASPNETCORE_URLS=http://0.0.0.0:9118

# Устанавливаем runtime + зависимости для Playwright/Chromium
RUN apk add --no-cache \
    dotnet8-runtime \
    icu-libs \
    chromium \
    nss \
    freetype \
    harfbuzz \
    ttf-freefont \
    ca-certificates

WORKDIR /app

# Копируем Lampac из официального образа
COPY --from=ghcr.io/lampac-talks/lampac:155.1-ce-amd64-finality /home /app

EXPOSE 9118