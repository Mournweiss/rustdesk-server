<div align="center">

# RustDesk Server Services

[![hbbs Documentation](https://img.shields.io/badge/docs-hbbs%2FREADME.md-blue?logo=readthedocs&style=flat-square)](./hbbs/README.md)
[![hbbr Documentation](https://img.shields.io/badge/docs-hbbr%2FREADME.md-blue?logo=readthedocs&style=flat-square)](./hbbr/README.md)
[![Official RustDesk Documentation](https://img.shields.io/badge/docs-rustdesk.com-blue?logo=readthedocs&style=flat-square)](https://rustdesk.com/docs/en/self-host/)

</div>

## Overview

This directory contains the service definitions and build instructions for the RustDesk self-hosted server components, designed for deployment as microservices.

## Included Services

-   **hbbr** — RustDesk Relay Server  
    Relays encrypted traffic between RustDesk clients, enabling connections across NAT and firewalls.

-   **hbbs** — RustDesk Broker Server  
    Handles client registrations, authentication, and coordination between clients and relay servers.

## Usage

These services are intended to be used with orchestration tool. See the root [`compose.yml`](../compose.yml) for an example of how to orchestrate both services together.
