# Day Trader for ChatGPT

A ChatGPT-oriented port of Jake Schincariol's MIT-licensed **day-trader-skill**.

This repository adapts the original Claude skill pack for use as a ChatGPT-assisted trading research workflow. The Python tools remain standalone: ChatGPT can help you choose commands, interpret their JSON/output, review setups, and enforce a human approval step.

## Safety first

- Paper trading is the default.
- No order should be submitted without an explicit user confirmation for the exact ticket.
- Run risk checks before any broker/execution step.
- Never paste brokerage API keys into chat. Keep secrets in environment variables.
- The Time Machine is a simulation, not a prediction.
- This project is software/research tooling, not financial advice.

## Modules

- `trader-scanner` — chart/setup scanner
- `trader-news` — news and SEC-event monitor
- `trader-entry` — entry timing
- `trader-exit` — stop/target planning
- `trader-timemachine` — historical/simulation reality check
- `trader-budget` — position sizing
- `trader-risk` — trade limits and PASS/BLOCK checks
- `trader-broker` — prepares execution tickets; explicit approval required
- `trader-alerts` — price/stop/target alerts
- `trader-analyst` — earnings/fundamental facts
- `trader-pelosi` — public congressional disclosure reader

## ChatGPT workflow

Ask ChatGPT to work through the repository in this order:

```
scanner -> news -> entry -> exit -> timemachine -> budget -> risk -> broker
```

A useful instruction is:

> Use this repository as my day-trading research workflow. Start with paper trading. Never place or recommend submitting an order unless the risk check passes and I explicitly approve the exact order. Show entry, stop, target, dollar risk, position size, reward/risk and key assumptions before asking for approval.

The Python tools require Python 3.8+ and use public/free data sources. See each module and its command-line help for options.

## Example commands

```bash
python3 trader-scanner/scan.py universe
python3 trader-scanner/scan.py daily
python3 trader-scanner/scan.py orb --at 10:15
python3 trader-news/news.py --tickers TSLA --hours 12
python3 trader-entry/entry.py check TSLA --setup orb
python3 trader-exit/exit.py plan --stop or-mid --target 1R --write
python3 trader-timemachine/timemachine.py run --write
python3 trader-budget/size.py --write
python3 trader-risk/check.py
python3 trader-broker/ticket.py show
python3 trader-alerts/alerts.py check
python3 trader-analyst/facts.py TSLA
python3 trader-pelosi/ptr.py index --member pelosi
```

## SEC identification

SEC-facing tools require a descriptive user agent. Configure `SEC_USER_AGENT` in your environment rather than posting personal information in chat.

## Attribution

This project is derived from **The Day Trader skill** by Jake Schincariol:
https://github.com/Jakeschincariol/day-trader-skill

Original project and code are MIT licensed. The upstream LICENSE is retained in this repository. This ChatGPT port is not affiliated with or endorsed by OpenAI or the upstream author.

## Disclaimer

Day trading can result in substantial losses. Public/free market data may be delayed, incomplete, rate-limited, or incorrect. Stops are not guaranteed execution prices. Verify anything material with your broker and consider professional financial/tax advice where appropriate.
