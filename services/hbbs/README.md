<div align="center">

# RustDesk Broker Server

[![hbbr Documentation](https://img.shields.io/badge/docs-hbbr%2FREADME.md-blue?logo=readthedocs&style=flat-square)](../hbbr/README.md)
[![Services Overview](https://img.shields.io/badge/docs-services%2FREADME.md-blue?logo=readthedocs&style=flat-square)](../README.md)
[![Official RustDesk Documentation](https://img.shields.io/badge/docs-rustdesk.com-blue?logo=readthedocs&style=flat-square)](https://rustdesk.com/docs/en/self-host/)

</div>

## Overview

This service provides a containerized RustDesk Broker Server (hbbs), which acts as the central coordination point for RustDesk clients and relays.

## Key Features

-   Manages client registrations and connections
-   Coordinates communication between RustDesk clients and relay servers (hbbr)
-   Essential for enabling remote desktop access in a self-hosted RustDesk environment

## Usage

This container is intended to be run as part of a Compose setup. Example section in [`compose.yml`](../../compose.yml):

```yaml
hbbs:
    build:
        context: ./services/hbbs
    image: rustdesk-hbbs:latest
    container_name: rustdesk-hbbs
    restart: unless-stopped
    working_dir: /data
    ports:
        - "21115:21115"
        - "21116:21116"
        - "21116:21116/udp"
        - "21118:21118"
    env_file:
        - .env
    volumes:
        - ./data:/data
    command: ["-r", "${HBBS_RELAY_ADDR}"]
    networks:
        - rustdesk-net
```

## Exposed Ports

-   **21115** — Main broker server port
-   **21116** — Secondary port (TCP/UDP) for client connections
-   **21118** — Additional communication port

## Environment Variables

Use a `.env` file to provide required environment variables, such as `HBBS_RELAY_ADDR` for relay server address.
