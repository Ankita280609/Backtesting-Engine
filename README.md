# WQ Brain FEL Backtesting Engine

[cite_start]A self-hosted, high-performance backtesting engine designed to replicate and extend the WorldQuant Brain platform environment[cite: 522]. [cite_start]It parses and evaluates Fast Expression Language (FEL) alpha signals locally against historical market data, providing researchers with sub-second iteration cycles and fully transparent performance metrics[cite: 524].

## 🚀 Core Objectives
* [cite_start]**Local FEL Execution:** Compile and execute raw FEL expressions into fully vectorized NumPy/Numba operations[cite: 524, 608].
* [cite_start]**Transparent Metrics:** Reproduce Brain-style evaluation metrics including Sharpe, Fitness, Information Coefficient (IC), and Turnover[cite: 524].
* [cite_start]**Advanced Portfolio Logic:** Support single-alpha and multi-alpha portfolio modes with custom neutralization (Market/Sector/Industry), linear decay, and truncation[cite: 677, 679].
* [cite_start]**High-Speed Iteration:** Process thousands of parameter variations in bulk using a highly optimized local data pipeline[cite: 526].

## 🏗️ System Architecture
[cite_start]The engine operates on a clean, multi-layered architecture[cite: 549]:
1. [cite_start]**Data Infrastructure:** Ingests OHLCV and fundamentals into partitioned Parquet files, queried via DuckDB with Redis caching[cite: 564, 565, 566].
2. [cite_start]**FEL Expression Engine:** A 4-stage pipeline (Lexer -> Parser -> AST -> Evaluator) built with Lark that maps strings to array operations[cite: 586, 587].
3. [cite_start]**Operator Library:** A comprehensive suite of cross-sectional and time-series operators (e.g., `ts_mean`, `rank`, `neutralize`) accelerated by Numba JIT[cite: 614, 616, 627].
4. [cite_start]**Backtesting Core:** Simulates daily P&L, applies trading costs, and enforces risk limits[cite: 647, 696].
5. [cite_start]**REST API & UI:** A FastAPI backend serving a React/Vite dashboard for expression editing, visualization, and alpha management[cite: 551].

## 💻 Tech Stack
* [cite_start]**Core Numerics:** Python 3.11, NumPy, Numba, SciPy [cite: 506, 746]
* [cite_start]**Data Layer:** Pandas, Polars, PyArrow, DuckDB, Redis [cite: 746]
* [cite_start]**Parser:** Lark [cite: 746]
* [cite_start]**API & Frontend:** FastAPI, React, Recharts, Monaco Editor [cite: 746]
