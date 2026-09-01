<div align="center">

# Stark

**Real-time chat infrastructure, built to survive production.**

[![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)](#)
[![WebSocket](https://img.shields.io/badge/WebSocket-000000?style=flat-square&logo=socket.io&logoColor=white)](#)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](#)

</div>

---

## Overview

Stark is a real-time chat system built on a hybrid **HTTP API + WebSocket** architecture, backed by a shared PostgreSQL store. It's engineered for the parts most chat demos skip — connection scaling, message integrity, and graceful failure — not just the happy path.

No frameworks doing the thinking for you. Every layer — transport, auth, persistence — is understood, not assumed.

---

## Architecture

```
┌─────────────┐       ┌──────────────┐       ┌─────────────┐
│   Client    │──────▶│  HTTP API    │──────▶│             │
│             │       │  (REST)      │       │             │
│             │       └──────────────┘       │  PostgreSQL │
│             │       ┌──────────────┐       │             │
│             │◀─────▶│  WS Server   │──────▶│             │
└─────────────┘       │  (real-time) │       └─────────────┘
                       └──────────────┘
```

- **HTTP API** — auth, resource management, group/message operations
- **WS Server** — real-time delivery, presence, typing indicators
- **Shared DB layer** — single source of truth across both surfaces

---

## Core Features

| Capability | Detail |
|---|---|
| **Messaging** | Real-time delivery over WebSocket, with pinning and deletion controls |
| **Groups** | Full group management — creation, membership, roles |
| **Auth** | JWT-based, with refresh token rotation |
| **Scaling** | Sticky sessions + pub/sub for horizontal WS scaling |
| **Security** | TLS/SSL enforced, CSRF/CORS hardened |
| **Persistence** | PostgreSQL, schema optimized for chat access patterns |

---

## Engineering Principles

- **Backpressure-aware** — WS framing and buffering handled explicitly, not left to chance
- **Stateless where it matters** — horizontal scaling isn't bolted on, it's designed in
- **Fail loud, fail safe** — connection drops and reconnections are first-class, not edge cases
- **No magic** — every abstraction earns its place by solving a real problem

---

## Tech Stack

`Node.js` · `WebSocket (ws)` · `PostgreSQL` · `JWT` · `TLS/SSL` · `Redis (pub/sub)`

---

## Status

Actively developed. Production-oriented from day one — not a prototype pretending to scale.

---

<div align="center">

**Built by Yash Choudhary**
*Systems Engineer · Real-time Architect*

</div>
