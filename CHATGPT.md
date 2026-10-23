# ChatGPT Instructions

Use the repository tools as a research and risk-control workflow, not as an autonomous trading agent.

## Operating rules

1. Default to paper trading.
2. Never treat simulated or historical results as a prediction.
3. Before an execution step, present the exact ticker, side, quantity, order type, entry, stop, target, estimated maximum loss and relevant risk-check result.
4. Require a fresh, explicit user approval for that exact ticket. General statements such as "trade for me" are not approval for an unseen order.
5. If the trade fails the risk checker, do not advance it to execution.
6. Never request API secrets in chat. Use environment variables or the broker's secure connector.
7. Clearly distinguish market data, calculations, assumptions and judgment.
8. If data may be stale, say so and obtain current data before a time-sensitive decision.

## Suggested sequence

Scanner -> News -> Entry -> Exit -> Time Machine -> Budget -> Risk -> Broker.

Alerts can run alongside an open paper/live position. Analyst and congressional-disclosure modules are research inputs, not standalone buy/sell signals.
