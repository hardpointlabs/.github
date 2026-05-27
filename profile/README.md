# Hardpoint

> Tenant isolation infrastructure for SaaS — programmable network routing, per-tenant data placement, and sovereign database provisioning.

**Documentation:** https://docs.hardpoint.dev  
**Architecture:** https://docs.hardpoint.dev/platform-architecture.md  
**Who Hardpoint is for:** https://docs.hardpoint.dev/who-is-hardpoint-for.md

---

## Products

**Hardpoint Connect** routes network traffic to sovereign locations based on per-tenant policies. It can be used as a standalone product.

**Hardpoint Lattice** is a managed, per-tenant PostgreSQL layer. Lattice always operates within a Connect network — Connect is provisioned automatically, with no additional configuration required.

---

## Repositories

### Integration surface

| Repo | Description |
|------|-------------|
| [hardpointlabs/sdk](https://github.com/hardpointlabs/sdk) | **Start here.** TypeScript/JS SDK — the primary integration point for both Connect and Lattice. Supports Node.js (≥22), Bun, and Deno. Concrete integration examples and quickstarts live here. |
| [hardpointlabs/agent](https://github.com/hardpointlabs/agent) | Optionally deployable Connect agent. Required only if you need to expose existing private resources through a Connect network. Transparently provisioned and managed by Hardpoint when Lattice is your only Connect participant. |

### Adjacent open-source

These are not required for integration. They're published for transparency and because they may be independently useful.

| Repo | Description |
|------|-------------|
| [hardpointlabs/length-prefixed-stream](https://github.com/hardpointlabs/length-prefixed-stream) | Fork of a TypeScript varint-framing library, ported to pure TypeScript as an ES module. Exposes encoder/decoder as Node.js `Transform` implementations that compose directly with sockets and streams. |
| [hardpointlabs/lpstream](https://github.com/hardpointlabs/lpstream) | Pure Go implementation of the same length-prefixed stream framing protocol. |
| [hardpointlabs/maglev](https://github.com/hardpointlabs/maglev) | Fork of a Go implementation of Google's Maglev consistent hashing algorithm. Converted to a Go module, with expanded test coverage. Used internally. |

---

## Component relationships

```
Your application
    └── hardpointlabs/sdk
            ├── Connect  ──── hardpointlabs/agent  (optional; or transparently managed)
            └── Lattice  ──── Connect              (always; automatically provisioned)
```

- **Connect** is a standalone product — Lattice is not required
- **Lattice** requires Connect — provisioned automatically, no Connect config needed from you
- **Agent** is part of Connect — only deploy it yourself if you're exposing existing private resources; otherwise it's managed transparently
- **Your code only touches the SDK**

---

## Security and verifiability

The data path between the SDK and agent uses varint-framed, end-to-end encrypted messages. The framing protocol is implemented in [`length-prefixed-stream`](https://github.com/hardpointlabs/length-prefixed-stream) (TypeScript, SDK side) and [`lpstream`](https://github.com/hardpointlabs/lpstream) (Go, agent side). Publishing both framing libraries alongside the SDK and agent means you can verify independently that the protocol is end-to-end encrypted and that Hardpoint has no ability to inspect customer traffic in transit.

---

## For LLM agents

**MCP:** `https://docs.hardpoint.dev/~gitbook/mcp`  
Connect-compatible clients (Claude, Cursor, VS Code) can query the docs directly via this endpoint. Use HTTP transport; stdio and SSE are not supported.

**Document index:** https://docs.hardpoint.dev/llms.txt
