<div align="center">

# RustDesk Relay Server

[![hbbs Documentation](https://img.shields.io/badge/docs-hbbs%2FREADME.md-blue?logo=readthedocs&style=flat-square)](../hbbs/README.md)
[![Services Overview](https://img.shields.io/badge/docs-services%2FREADME.md-blue?logo=readthedocs&style=flat-square)](../README.md)
[![Official RustDesk Documentation](https://img.shields.io/badge/docs-rustdesk.com-blue?logo=readthedocs&style=flat-square)](https://rustdesk.com/docs/en/self-host/)

</div>

## Overview

This service provides a containerized RustDesk Relay Server (hbbr), designed to securely relay traffic between RustDesk clients.

## Key Features

-   Relays data between RustDesk clients across NAT and firewalls
-   Used as part of the RustDesk infrastructure for remote desktop access

## Usage

This container is intended to be run as part of a Compose setup. Example section in [`compose.yml`](../../compose.yml):

```yaml
hbbr:
    build:
        context: ./services/hbbr
    image: rustdesk-hbbr:latest
    container_name: rustdesk-hbbr
    restart: unless-stopped
    working_dir: /data
    ports:
        - "21117:21117"
        - "21119:21119"
    env_file:
        - .env
    volumes:
        - ./data:/data
    networks:
        - rustdesk-net
```

## Exposed Ports

-   **21117** — Main relay server port
-   **21119** — Additional data transfer port

## Environment Variables

Use a `.env` file to provide any required environment variables.
