# First prototype: one market, one Bitsocial thread

**Status:** proposed experiment, open for a contributor to lead.

Build a page that makes one existing prediction market and its Bitsocial discussion useful
together. The first Trueo experiment can be a standalone client or a prototype in an existing
Bitsocial app. The [Trueo research note](research/trueo.md) identifies the integration unknowns.

## Participant experience

1. Open a shareable page and read the market question, deadline, resolution rules, and sources.
2. See the market's current state and a timestamp for the last successful refresh.
3. Read or contribute to the associated Bitsocial discussion without connecting a trading wallet.
4. Follow a clearly identified link to the existing trading interface.
5. Return to the thread as evidence appears and the market progresses toward resolution.

This establishes a useful first milestone before adding native wallet transactions. A later
iteration can show an executable quote, let the participant review and sign a transaction, and
display a confirmed position.

## Suggested implementation boundaries

| Part | First implementation |
| --- | --- |
| Market identity | An explicit chain identifier and market contract address, plus the protocol/deployment version where needed. |
| Discussion identity | A reference to an existing Bitsocial community and thread using the current client APIs. |
| Linking | Begin with an ordinary market link in a post. Investigate existing link metadata before proposing new shared fields. |
| Market data | A small reader for question, rules, token identifiers, deadline, and lifecycle state. Label stale or unavailable data. |
| Social data | Fetch and publish through existing Bitsocial tooling, applying the community's normal publishing challenges. |
| Trading | Link to the market initially. Add a wallet flow once contract interfaces and transaction behavior are understood. |

Multiple communities may discuss the same market. They should reference the same settlement
contracts; the prototype does not need to mint a new market for each thread. A comment expressing
"YES" is an opinion. A claimed financial position needs a separate verification design.

## Completion criteria

- A contributor can reproduce the demo from documented setup instructions.
- The displayed market identity, rules, and state can be checked against its documented source.
- A real Bitsocial thread can be read and published to from the demo.
- The same thread remains readable in another compatible client.
- Missing market data produces a clear unavailable/stale state while discussion remains usable.
- Proposed, disputed, cancelled, and finalized outcomes are represented without conflating them;
  fixtures are acceptable for lifecycle states that are unavailable in the selected live market.
- The prototype documents the services it depends on and which parts have actually been tested.

For an optional trading iteration, verify quote expiry, fees, slippage, approvals, rejected and
failed transactions, confirmation, and redemption behavior in a suitable test environment before
calling the flow complete.

## What the community experiment should establish

Choose a real community and question. Record why participants want this market, the expected
trade sizes, available liquidity, and the criteria they will use to evaluate the experience.
Observe repeat visits, substantive discussion, and whether participants can trade as intended.
Report friction and failed assumptions as well as successful interactions.

Useful results include finding that a simple market card is enough, that a dedicated client is
worth building, or that the proposed community lacks sufficient demand. The experiment should
make the next decision easier.
