# On-chain forensics

I re-measure the crypto numbers everyone else copies, and report the gap upstream where it can be fixed.

**Method:** each finding states its source and how it was measured, pins on-chain reads to a block where that is possible, marks figures that could only be recorded, and names what would prove it wrong.

I choose what to measure, decide what is published, and answer for the conclusions. I use AI agents to draft text and code and to run the checks.

## Public findings

Some of these have reproductions, with the data and checks you can run yourself, in [onchain-findings](https://github.com/shyhaeky95/onchain-findings).

| Where | What was wrong | Outcome |
|---|---|---|
| [DefiLlama · Uniswap v4 fees, Robinhood Chain](https://github.com/DefiLlama/dimension-adapters/issues/8242) | Daily fees overstated ~3.9×: every swap was priced in currency0, including thin meme pairs | Fixed in [#8376](https://github.com/DefiLlama/dimension-adapters/pull/8376). The maintainer's re-run matched my figure to about 2% |
| [DefiLlama · Uniswap v4 TVL, BSC](https://github.com/DefiLlama/DefiLlama-Adapters/issues/20659) | ~$5.6B of reported TVL came from one token whose two price sources differed by ~2.5×10⁸ · [reproduction](https://github.com/shyhaeky95/onchain-findings/tree/main/findings/20659-defillama-uniswap-v4-bsc) | Fixed in [#20690](https://github.com/DefiLlama/DefiLlama-Adapters/pull/20690) |
| [DefiLlama · NEAR revenue](https://github.com/DefiLlama/dimension-adapters/issues/9676) | Revenue before 2026-06-19 still counted 100% of gas fees, overstating it by $5.37M | History refilled |
| [DefiLlama · Rocket Pool fees](https://github.com/DefiLlama/dimension-adapters/issues/8812) | Saturn 1 megapool reward deposits were skipped: 78.23 ETH of rETH rewards missing · [reproduction](https://github.com/shyhaeky95/onchain-findings/tree/main/findings/8812-defillama-rocketpool-megapools) | Fixed in [#8833](https://github.com/DefiLlama/dimension-adapters/pull/8833) |
| [DefiLlama · Uniswap v3, Robinhood Chain](https://github.com/DefiLlama/dimension-adapters/issues/8480) | Chain missing from the fee-switch config, so holders revenue was empty | Fixed in [#8484](https://github.com/DefiLlama/dimension-adapters/pull/8484) |
| [DefiLlama · Uniswap v3, Unichain](https://github.com/DefiLlama/dimension-adapters/issues/8849) | Missing fee-switch date, so holders revenue was reported as 0 | Fixed in [#9069](https://github.com/DefiLlama/dimension-adapters/pull/9069) |
| [Sky · Atlas A.2.3.1.2.4](https://github.com/sky-ecosystem/next-gen-atlas/issues/306) | 976,150.62 SKY bought back by the Smart Burn Engine, with no reduction in `totalSupply` · [reproduction](https://github.com/shyhaeky95/onchain-findings/tree/main/findings/306-sky-atlas-burn) | Answered: to be burned in a future executive vote |
| [Hyperliquid · public EVM RPC](https://github.com/hyperliquid-dex/node/issues/158) | `eth_call` and `eth_getCode` return latest state when asked for a block the endpoint does not support | Open |
| [Stellar · dashboard](https://github.com/stellar/dashboard/issues/363) | `sdfMandate` sums 15 accounts; the Lumens docs and Mandate page list 13 | Open |
| [DefiLlama · pump.fun volume history](https://github.com/DefiLlama/dimension-adapters/issues/10310) | Stored daily volume ran at a median 0.72 of the fee-implied level from 2025-06-11 to 2026-10-08, an estimated $12.8B difference; refill requested | Open |
| [DefiLlama · Pump parent totals](https://github.com/DefiLlama/dimension-adapters/issues/10311) | Parent totals include the doublecounted Mobile App listing: 7.03% of reported September revenue | Open |
| [DefiLlama · SSV operator fees](https://github.com/DefiLlama/dimension-adapters/issues/10312) | ETH operator fees are weighted by validator count instead of effective balance: ~28–34% low per day (18–20 Oct 2026) | Open |

---

*Private activity on this profile is a daily measurement desk. Public findings land upstream first.*
