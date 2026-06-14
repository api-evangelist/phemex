# Phemex

Phemex is a cryptocurrency derivatives exchange offering REST and WebSocket APIs for spot trading, perpetual contracts, hedged perpetual contracts, futures, asset transfers, and real-time market data.

## APIs

| API | Description | Documentation |
|-----|-------------|---------------|
| Contract Trading API | Perpetual contract trading, position management, and market data | [Docs](https://github.com/phemex/phemex-api-docs/blob/master/Public-Contract-API-en.md) |
| Spot Trading API | Spot order management, wallet queries, and market data | [Docs](https://github.com/phemex/phemex-api-docs/blob/master/Public-Spot-API-en.md) |
| Hedged Perpetual API | Simultaneous long/short positions with independent leverage | [Docs](https://github.com/phemex/phemex-api-docs/blob/master/Public-Hedged-Perpetual-API.md) |
| Asset Transfer API | Transfers between spot/futures accounts and sub-accounts | [Docs](https://github.com/phemex/phemex-api-docs/blob/master/Public-Transfer-API-en.md) |

## Base URLs

| Environment | REST | WebSocket |
|-------------|------|-----------|
| Production | `https://api.phemex.com` | `wss://phemex.com/ws` |
| VIP/High Rate | `https://vapi.phemex.com` | `wss://vapi.phemex.com/ws` |
| Testnet | `https://testnet-api.phemex.com` | `wss://testnet.phemex.com/ws` |

## Authentication

All private REST endpoints require three headers:
- `x-phemex-access-token` — API key
- `x-phemex-request-expiry` — Unix epoch seconds (now + 60 seconds)
- `x-phemex-request-signature` — `HMacSha256(URL Path + QueryString + Expiry + body)` signed with API secret

WebSocket private data access requires sending `user.auth` with token, signature, and expiry.

## Rate Limits

| Tier | Contract | SpotOrder | Others | IP Limit |
|------|----------|-----------|--------|----------|
| Standard | 500/min | 500/min | 100/min | 5000/5min |
| VIP/VAPI | 5000/min | 500/min | 100/min | 5000/5min |

WebSocket: max 5 concurrent connections, 20 subscriptions per connection, 20 requests/second.

## Resources

- [API Documentation Repository](https://github.com/phemex/phemex-api-docs)
- [CCXT SDK](https://github.com/ccxt/ccxt)
- [Java Client](https://github.com/phemex/java-client)
- [Error Codes](https://github.com/phemex/phemex-api-docs/blob/master/TradingErrorCode.md)
- [Help Center](https://phemex.com/help-center)
- [Fees & Conditions](https://phemex.com/fees-conditions)
- [Testnet](https://testnet.phemex.com)
