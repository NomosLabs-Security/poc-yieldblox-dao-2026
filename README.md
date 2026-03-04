# YieldBloxDAO — VWAP Oracle Manipulation Lending Pool Exploit — PoC

> **Educational Purpose Only** — This PoC is created solely for security
> research and educational purposes. It simulates the vulnerability locally.

## Quick Start

```bash
git clone https://github.com/NomosLabs-Security/poc-yieldblox-dao-2026
cd poc-yieldblox-dao-2026
forge install foundry-rs/forge-std --no-git
forge test -vvvv
```

## Details

- **Exploit Date:** 2026-02-22
- **Chain:** Stellar (Blend Protocol) — simulated in EVM
- **Oracle:** Reflector (VWAP-based)
- **Expected Output:** ~$10.2M drained via oracle-manipulated overcollateralization
- **Full Analysis:** [NomosLabs Security Intelligence Archive](https://nomoslabs.io/archive/yieldblox-dao-2026)

## Description

The attacker exploited thin liquidity in the USTRY/USDC market on Stellar's DEX. The Reflector oracle used a Volume-Weighted Average Price (VWAP) model. When the sole market maker withdrew liquidity, the VWAP window had zero trading activity. A single malicious trade (0.05 USTRY at $106) inflated USTRY's price 100x — from $1.05 to $106.

Using the inflated collateral value, the attacker borrowed the pool's entire reserves: ~1M USDC + 61.25M XLM (~$10.2M total). Stellar validators later froze ~48M XLM ($7.2M).

## License

MIT — For educational use only.
