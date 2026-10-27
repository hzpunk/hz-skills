---
name: pybroker-quant
description: "Algorithmic trading and quantitative backtesting in Python using PyBroker: ML model integration, walk-forward analysis, and risk metrics."
---

# PyBroker Quant (`/pybroker-quant`)

Количественный анализ, бэктестинг алгоритмических стратегий и машинное обучение для финансовых рынков на Python.

## Ключевые возможности:
- Высокоскоростной векторизованный бэктестинг с защитой от lookahead bias.
- Walk-forward оптимизация и кросс-валидация торговых гипотез.
- Расчет метрик риска: Sharpe, Sortino, Max Drawdown, Calmar.

## Пример стратегии на Python:
```python
import pybroker
from pybroker import Strategy, YFinance

def init(ctx):
    ctx.options(fee_pct=0.001)

def buy_low(ctx):
    # Логика входа при падении цены ниже скользящей средней
    if not ctx.long_pos() and ctx.bars.close[-1] < ctx.bars.open[-1]:
        ctx.buy_shares = 100

strategy = Strategy(YFinance(), start_date='2024-01-01', end_date='2026-01-01')
strategy.add_execution(buy_low, ['AAPL', 'MSFT'])
result = strategy.backtest()
print(result.metrics)
```
