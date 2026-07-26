---
name: Run an LSO API as an MCP server
description: Blend a Mplify/MEF LSO API with its product payloads and expose it to an agent as MCP tools using the mplify-mcp-server runner shipped in every LSO SDK.
api: mcp/mef-mcp.yml
apis:
  - mcp/mef-mcp.yml
  - mcp/mef-tool-crosswalk.yml
operations:
  - createProductOrder
  - retrieveProductOrder
  - listProductOrder
  - createQuote
  - listProduct
generated: '2026-07-25'
method: generated
source: https://github.com/MEF-GIT/MEF-LSO-Sonata-SDK/blob/kylie/generated/mcp/MPLIFY-MCP-QUICKSTART.md
---

# Run an LSO API as an MCP server

From the **kylie** release (2026-02-17) onward, every Mplify LSO SDK ships MCP server code for
every Seller-side API. Mplify does **not** host an MCP endpoint — you run it, pointed at a Seller's
implementation.

## Steps

1. **Get the SDK.** Clone the IRP you need
   (`MEF-LSO-Sonata-SDK`, `Cantata`, `Interlude`, `Legato`, `Allegro`) at tag `kylie`, or download
   the release zip from https://lso.mplify.net/lso-api-sdk-releases. Work from `generated/mcp`.
2. **Blend the API with your payloads** (optional but usual). https://lso.mef.net/api-blender
   produces a downloadable API document with the product/service schemas you actually buy or sell
   folded in — the MCP server's tool schemas are only as specific as the document you feed it.
3. **Build the runner.** `docker build -t mplify-mcp-server mplify-mcp-runner`
4. **Configure one API.** Each API has an env file — `PRODUCT_ORDER.env`, `QUOTE.env`,
   `TROUBLE_TICKET_MANAGEMENT.env`, `ALARM_MANAGEMENT.env`, … Set:
   - `MCP_OAS_URI` — path to the (blended) API document, e.g. `/data/order/productOrderManagement.api.yaml`
   - `MCP_SERVER_URI` — the **Seller's real base URL**, replacing the `{serverBase}` template
   - `MCP_AUTH_MODE` — `basic` or `oauth-refresh`; the shipped `user:password` is a placeholder
   - For OAuth: `MCP_OAUTH_TOKEN_URL`, `MCP_OAUTH_CLIENT_ID`, `MCP_OAUTH_CLIENT_SECRET`,
     `MCP_OAUTH_REFRESH_TOKEN`, `MCP_OAUTH_SCOPE`
5. **Run it.**
   `docker run --rm -p 8004:8000 -v $(pwd):/data --env-file ./PRODUCT_ORDER.env mplify-mcp-server`
   The server listens at `http://localhost:8004/mcp`. Give each API its own port — the quickstart
   allocates 8000-8012.
6. **Inspect the tools.** `npx @modelcontextprotocol/inspector http://localhost:8004/mcp`. One tool
   per OpenAPI operation, named after the operationId, with the operation's parameters and
   requestBody as its input schema. The full binding is in `mcp/mef-tool-crosswalk.yml`.
7. **Wire it to an agent.** Add the URL to your VS Code user `mcp.json` or to Claude Desktop's
   `mcpServers` block.

## Rules

- **Never expose a write-capable LSO tool set without scoping the credentials.** `createProductOrder`
  and `createCancelProductOrder` are real commercial commitments to a partner. Give the container an
  identity whose OAuth scopes (see `scopes/mef-scopes.yml`) cover only the operations the agent may
  perform, and prefer read-only APIs (Product Catalog, Product Inventory, Service Inventory) for
  exploratory agents.
- **Notification/listener APIs have no MCP server** and should not be given one — they are inbound
  callback contracts, not tools you call.
- The `{serverBase}` template must be replaced with a real Seller host. Do not point the runner at
  `mplify.net`; Mplify runs no API.
