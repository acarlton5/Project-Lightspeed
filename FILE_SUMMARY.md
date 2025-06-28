# Project Lightspeed File Overview

This document briefly describes the purpose of the main files in this repository.

## Root
- `README.md` - Overall project documentation and installation steps.
- `LICENSE` - MIT license information.
- `.env` - Example environment variables used with Docker Compose.
- `docker-compose.yml` - Docker Compose file that starts ingest, webrtc and frontend containers.

## Contrib
- `contrib/ubuntu_installer/README.md` - Instructions for the community Ubuntu installer.
- `contrib/ubuntu_installer/ubuntu_installer.sh` - Optional script to install dependencies on Ubuntu.

## Ingest (Rust)
- `ingest/README.md` - Docs for the ingest server.
- `ingest/Cargo.toml` - Rust crate configuration.
- `ingest/Dockerfile` - Docker image for building/running the ingest server.
- `ingest/src/main.rs` - Application entry. Opens a TCP listener and spawns tasks for each client.
- `ingest/src/connection.rs` - Manages individual FTL connections and parses protocol commands.
- `ingest/src/ftl_codec.rs` - Tokio codec implementing the FTL handshake protocol.
- `ingest/src/cli.yml` - CLI option definitions consumed by clap.

## WebRTC (Go)
- `webrtc/README.md` - Docs for the WebRTC server.
- `webrtc/go.mod` / `go.sum` - Go module files listing dependencies.
- `webrtc/Dockerfile` - Docker image for the WebRTC service.
- `webrtc/main.go` - Receives RTP on UDP and serves it to browsers over WebRTC.
- `webrtc/internal/signal` - Helpers for SDP exchange and base64 compression.
- `webrtc/ws` - WebSocket hub used for exchanging offers, answers and ICE candidates.

## Frontend (React)
- `frontend/README.md` - Docs for the React application.
- `frontend/package.json` - Node package manifest.
- `frontend/Dockerfile` - Builds and serves the static website.
- `frontend/public` - Static assets (HTML, config, icons) served directly by Nginx.
- `frontend/src/index.js` - Entry point that renders the React app.
- `frontend/src/App.js` - Main page layout connecting components.
- `frontend/src/components` - Individual React components such as the video player and header.
- `frontend/src/context` - React context providers for WebSocket and RTCPeerConnection state.
- `frontend/src/styles` - Styled‑Components definitions for page styling.


