<div align="center">

# RustDesk Server

[![Official RustDesk Documentation](https://img.shields.io/badge/docs-rustdesk.com-blue?logo=readthedocs&style=flat-square)](https://rustdesk.com/docs/en/self-host/)
[![RustDesk Server Source Code](https://img.shields.io/badge/source-github.com%2Frustdesk%2Frustdesk-blue?logo=github&style=flat-square)](https://github.com/rustdesk/rustdesk)
[![License: AGPL v3](https://img.shields.io/badge/license-AGPL--v3-blue.svg?style=flat-square)](./LICENSE)

</div>

## Overview

RustDesk is an open-source remote desktop solution. This project packages the official RustDesk server components for easy deployment using Docker Compose or compatible orchestration tool.

-   **hbbs** — Broker Server: Handles client registrations, authentication, and coordination.
-   **hbbr** — Relay Server: Relays encrypted traffic between clients, enabling NAT traversal.

## Requirements

-   A **static public IP address** or a **domain name** is required for clients to reliably connect to your server.
-   The following ports must be forwarded from your router/firewall to the host running the containers:
    -   **21115** (TCP)
    -   **21116** (TCP/UDP)
    -   **21117** (TCP)
    -   **21118** (TCP)
    -   **21119** (TCP)
-   Ensure your firewall allows inbound connections on these ports.

## Quick Start

1. **Clone the repository:**

    ```bash
    git clone https://github.com/Mournweiss/rustdesk-server.git
    cd rustdesk-server
    ```

2. **Configure environment variables:**

    - Copy `.env.example` to `.env` and adjust as needed.

        ```bash
        cp .env.example .env
        ```

    - Set the `HBBS_RELAY_ADDR` variable with your server's public IP address or domain name (without port).

3. **Start the services:**

    ```bash
    podman-compose up -d
    ```

4. **Access:**
    - Clients can now connect to your server using the public IP/domain and the exposed ports.

## Directory Structure

-   [`services/`](./services/) — Contains build files and documentation for each service:

    -   [`hbbs/`](./services/hbbr/) — Relay server
    -   [`hbbr/`](./services/hbbs/) — Broker server

-   [`compose.yml`](./compose.yml) — Compose configuration

## License

This project packages and distributes the official RustDesk server components. See [RustDesk License](https://github.com/rustdesk/rustdesk/blob/master/LICENCE).
