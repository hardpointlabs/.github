# Hardpoint

> Tenant isolation infrastructure for SaaS — programmable network routing, per-tenant data placement, and sovereign database provisioning.

* **Documentation:** https://docs.hardpoint.dev
* **Architecture:** https://docs.hardpoint.dev/platform-architecture
* **Who Hardpoint is for:** https://docs.hardpoint.dev/who-is-hardpoint-for

---

## Products

**Invar** a lightweight open-source document database with Redis and incubating Mongo Wire Protocol compatibility.

**Invar Cloud** fully managed Invar data platform

**Hardpoint Enterprise** extends Invar Cloud with compliance-focused governance, security and audit features for customers deploying in on-prem/hybrid environments

---

## Repositories

### Invar

You can run Invar locally or in production yourself; all you need is the supplied container images


### Integration point

| Repo | Description |
|------|-------------|
| [hardpointlabs/sdk](https://github.com/hardpointlabs/sdk) | **Start here.** TypeScript/JS SDK — the primary integration point for Invar Cloud. Supports Node.js (≥22), Bun, and Deno. Concrete integration examples and quickstarts live here. |

### Adjacent open-source

These are not required for integration. They're published for transparency and because they may be independently useful.

| Repo | Description |
|------|-------------|
| [hardpointlabs/length-prefixed-stream](https://github.com/hardpointlabs/length-prefixed-stream) | Fork of a TypeScript varint-framing library, ported to pure TypeScript as an ES module. Exposes encoder/decoder as Node.js `Transform` implementations that compose directly with sockets and streams. |
| [hardpointlabs/lpstream](https://github.com/hardpointlabs/lpstream) | Pure Go implementation of the same length-prefixed stream framing protocol. |
| [hardpointlabs/maglev](https://github.com/hardpointlabs/maglev) | Fork of a Go implementation of Google's Maglev consistent hashing algorithm. Converted to a Go module, with expanded test coverage. Used internally. |

---

## Security and verifiability

The data path between the SDK and a database instance uses varint-framed, end-to-end encrypted messages. The framing protocol is implemented in [`length-prefixed-stream`](https://github.com/hardpointlabs/length-prefixed-stream) (TypeScript, SDK side) and [`lpstream`](https://github.com/hardpointlabs/lpstream) (Go, agent side). Publishing both framing libraries alongside the SDK and agent means you can verify independently that the protocol is end-to-end encrypted and that Hardpoint has no ability to inspect customer traffic in transit.

---

## For LLM agents

**MCP:** `https://docs.hardpoint.dev/~gitbook/mcp`  
Connect-compatible clients (Claude, Cursor, VS Code) can query the docs directly via this endpoint. Use HTTP transport; stdio and SSE are not supported.

**Document index:** https://docs.hardpoint.dev/llms.txt
