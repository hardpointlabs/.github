# Hardpoint Labs

> Data infrastructure for massive multi-tenancy.

**Product Documentation:** https://docs.hardpoint.dev

---

## Products

* **Invar:** a diskless document store with Redis™ compatibility
* **Invar Cloud:** fully managed Invar data platform
* **Hardpoint Enterprise:** extended infrastructure for Invar, supporting on-prem/hybrid environments, fleet management and compliance

---

## Repositories

### Invar

You can run Invar locally or in production yourself; all you need is the supplied container images.

| Repo | Description |
|------|-------------|
| [hardpointlabs/invar](https://github.com/hardpointlabs/invar) | **Start here.** The database itself |


### Integration point

| Repo | Description |
|------|-------------|
| [hardpointlabs/sdk](https://github.com/hardpointlabs/sdk) | TypeScript/JS SDK — the primary integration point for Invar Cloud. Supports Node.js (≥22), Bun, and Deno. Concrete integration examples and quickstarts live here. |

### Adjacent open-source

These are not required for integration. They're published for transparency and because they may be independently useful.

| Repo | Description |
|------|-------------|
| [hardpointlabs/length-prefixed-stream](https://github.com/hardpointlabs/length-prefixed-stream) | Fork of a TypeScript varint-framing library, ported to pure TypeScript as an ES module. Exposes encoder/decoder as Node.js `Transform` implementations that compose directly with sockets and streams. |
| [hardpointlabs/lpstream](https://github.com/hardpointlabs/lpstream) | Pure Go implementation of the same length-prefixed stream framing protocol. |
| [hardpointlabs/maglev](https://github.com/hardpointlabs/maglev) | Fork of a Go implementation of Google's Maglev consistent hashing algorithm. Converted to a Go module, with expanded test coverage. Used internally. |

---

## For LLM agents

**MCP:** `https://docs.hardpoint.dev/~gitbook/mcp`  
Connect-compatible clients (Claude, Cursor, VS Code) can query the docs directly via this endpoint. Use HTTP transport; stdio and SSE are not supported.

**Document index:** https://docs.hardpoint.dev/llms.txt
