# Connect to iKnow Blockchain with native Codex

September 26, 2026: iKnow Blockchain is one read-only connection for fourteen blockchains: Chia, Bitcoin, Ethereum, Solana, Zcash, Monero, NEAR, Base, Arbitrum One, OP Mainnet, Cosmos Hub, Cardano, Avalanche and Robinhood Chain. Production sign-in and real tool calls passed in native Codex. Access is invitation-only; other accounts need an invitation before this connection will work. This is a remote MCP connection, not an executable plugin ZIP or an approved store listing.

## Windows setup

1. Install/sign in to Codex using its normal instructions. No node, wallet software or private backend repository is required.
2. Merge the following entries into your Codex `config.toml` (normally `%USERPROFILE%\.codex\config.toml`). Preserve existing settings; do not duplicate an existing table. Put the top-level credentials-store setting before any table headers.

```toml
mcp_oauth_credentials_store = "keyring"

[mcp_servers.iknow-blockchain]
url = "https://mcp.iknowblockchain.com/mcp"

[mcp_servers.iknow-blockchain.oauth]
client_id = "14C4VTRF1mLTq4Z2j2iyHmnHWvXKjQHG"
callback_url = "http://127.0.0.1/callback/Pn6IQwp8T0Jp"
```

3. In PowerShell run `codex mcp login iknow-blockchain --scopes ikb:read,offline_access`. Follow the browser link, choose your invited account and accept read-only/offline access. Credentials are stored in Windows Credential Manager. Never paste a token into chat.
4. Start a fresh Codex session and ask: “Use iKnow Blockchain to check coverage, then convert 0.25 XCH to mojos.” Expected: fourteen chains in coverage and `250000000000` mojos.
5. Name the blockchain in each question. Developments are reviewed snapshots with dates and source links, not a live news feed. Public lookups return bounded pages of public data, never a whole wallet; Zcash shielded and Monero address holdings are private. Never provide a seed phrase or private key.

The registered callback is exact; no wildcard is used. If another Codex version/device emits a different callback, stop and contact support with that callback URL only (not the full authorization URL). Other host applications have separate registration requirements.

To disconnect, use `codex mcp logout iknow-blockchain` and remove only this server's config tables. Local logout removes the local credential; request account/service revocation separately if needed.

### Earlier Chia-only connection

The earlier `https://chia.iknowblockchain.com/mcp` connection (`chia:read`) remains available for existing users. New setups should use the connection above, which includes Chia.

## Troubleshooting

- `invitation_required` / 403 after sign-in: account is not enrolled. Contact support; signing in alone does not grant access.
- 401: sign in again; a wrong audience, expired or invalid token is rejected.
- 429: retry after the indicated delay. 503: service unavailable, not zero holdings.

Support: support@iknowblockchain.com. Feedback: feedback@iknowblockchain.com. Include host/version, OS, approximate time and prompt; omit authorization URLs, tokens and private wallet information. Native Codex and Claude are verified on this connection; other hosts are not claimed tested here.

Publisher: ZTOR Services Incorporated, Kansas, USA.

[Website](https://iknowblockchain.com/) · [Coverage by chain](https://iknowblockchain.com/#coverage) · [Privacy](https://iknowblockchain.com/privacy/) · [Terms](https://iknowblockchain.com/terms/) · [Help](https://iknowblockchain.com/support/)

Release candidate: invite-only connection. Backend source and credentials are not distributed. Not a vendor-approved listing. Apache-2.0 applies to original release materials; third-party sources and marks retain their rights.
