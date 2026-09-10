# Trueo: integration research and potential collaboration

**Research date:** 2026-09-10. **Status:** candidate; no agreed collaboration or tested integration.

This note preserves a possibility raised in an initial Bitsocial discussion: combine Trueo
markets with Bitsocial communities, either through an existing client or a dedicated app.
The descriptions below were checked against Trueo's official documentation on the research date.
They describe the documented design; deployed behavior still needs implementation-level checks.

## Why investigate Trueo

Trueo's documented onchain trading and market-resolution interfaces suggest a useful division
of work: Trueo supplies markets and settlement, while a Bitsocial client supplies community
discussion and discovery. That is an integration hypothesis, not a demonstrated product fit.

The potential collaboration is concrete: establish a supported way to read a market, display its
rules and lifecycle, link it to a Bitsocial thread, and eventually let participants trade from the
client. An independent contributor could own this work. It does not require Bitsocial Forge to
operate the resulting app.

## What the official documentation establishes

| Area | Documented behavior | Implication for an integration |
| --- | --- | --- |
| Deployment | Developer contracts are deployed on Base; markets have their own YES/NO tokens. | Identify the chain, market address, and deployment version. [Deployments](https://docs.trueo.com/deployments) |
| Market rules | Titles, resolution criteria, and sources are committed onchain at launch. | Display the actual market terms alongside discussion. [Introduction](https://docs.trueo.com/) |
| Trading | YES/NO outcome tokens trade onchain through a custom Uniswap v4 hook. | Investigate quotes, routing, and wallet calls before adding trading. [Trading](https://docs.trueo.com/trading) |
| Collateral | TYD is a USDC-backed ERC-4626 vault token powered by Yearn. | Distinguish TYD amounts from USDC amounts and inspect conversion behavior. [TYD](https://docs.trueo.com/True-Yield-Dollar) |
| Outcome tokens | Depositing 1 TYD mints 1 YES and 1 NO; the pair can redeem for 1 TYD before resolution. A winning token redeems for 1 TYD after a YES/NO resolution. | Model collateral, positions, and redemption separately. [Minting](https://docs.trueo.com/liquidity-provision) |
| Proposals | Anyone can propose a market through an AI-assisted workflow. | Community proposals are worth exploring. [Proposing markets](https://docs.trueo.com/proposing-markets) |
| Launch | Proposals enter a funding phase and must reach a threshold to become tradable. Contributions help establish opening prices and liquidity. | A proposal card needs a different state from a live market card. [Proposal funding](https://docs.trueo.com/proposal-funding) |
| Oracle | Disputes can escalate through an Oracle Council, TRUE holders, and attesters. | Show proposed and disputed outcomes distinctly from finalized results. [Optimistic oracle](https://docs.trueo.com/optimistic-oracle) |

## Permissionless proposals and resolution eligibility

The initial discussion emphasized markets that larger venues might refuse to list. Current Trueo
documentation qualifies that thesis: permissionless proposals remain subject to integrity and
resolution-eligibility standards. Noncompliant markets must resolve as cancelled. Trueo therefore
cannot be assumed to settle every possible question. The first community market needs to be
checked against the actual criteria. [Market integrity standards](https://docs.trueo.com/market-integrity-standards)

Immutable market text also leaves interpretation work for the resolution system. The resolution
documentation allows alternative sources when listed sources are unavailable, faulty, or
superseded by verifiable information from a dispute, and describes cancelled/draw outcomes.
A client must make the applicable rules and current outcome state accessible.
[Resolving markets](https://docs.trueo.com/resolving-markets)

The collaboration hypothesis remains worth testing: a community may value creating and discussing
its own markets, with independent social clients and clear settlement dependencies. Whether that
produces enough participation and liquidity is an open empirical question.

## Integration work still needed

- **Contract and data inventory:** inspect the current deployment references, contract ABIs,
  market discovery, events, and support for older market versions. Determine whether rules,
  quotes, and status can be read without a private API.
- **Trading path:** identify the supported quote and transaction interfaces, approvals, fees,
  slippage controls, and wallet/network handling. Find out whether a maintained SDK exists.
- **Complete lifecycle:** cover proposals, funding, trading, resolution proposals, disputes,
  finalization, cancellation, and redemption. Read parameters from the relevant deployment.
- **Availability:** document dependence on Trueo's website, indexers, RPC providers, and any
  hosted AI proposal service. Investigate what an independent app can replace or run itself.
- **Social mapping:** reference the same onchain market across clients and communities. Avoid
  duplicating its liquidity just to create another discussion thread.
- **Identity:** decide whether users can optionally associate a wallet with a Bitsocial identity.
  Keep discussion usable without a wallet. Any displayed position claim needs explicit consent
  and a documented verification method.
- **Community experiment:** identify who wants the market, who supplies initial liquidity, and
  what would count as a useful result.

These are research questions, not promises of current Trueo or Bitsocial integration support.

## Possible collaboration

A useful first exchange with Trueo would concern supported third-party clients, contract/data
interfaces, licensing of reusable components, and a small joint prototype. The proposed outcome
is one usable market with a Bitsocial thread and a community willing to try it.

Public contact and development starting points:

- [Trueo app](https://trueo.com/)
- [Official links and community channels](https://docs.trueo.com/official-links), including
  [@Trueo_](https://x.com/Trueo_) and [Discord](https://discord.gg/trueo)
- [Trueo GitHub organization](https://github.com/trueo-protocol)
- [Contract repository](https://github.com/trueo-protocol/trueo-contracts)

Record any future outreach outcome and agreed scope here. Contributors should describe their
own project and involvement accurately; this repository does not imply endorsement by Trueo.

## Scope of this note

The original discussion also covered TRUE's price, token supply, liquidity, exchange listings,
and possible catalysts. This repository preserves the product and collaboration opportunity.
It makes no claim about token valuation or returns. Buying TRUE is not a proposed prerequisite
for discussing markets or contributing to this project; any token requirements for particular
oracle operations should be documented as part of that integration work.
