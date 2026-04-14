# WQ Brain FEL Backtesting Engine

A self-hosted, high-performance backtesting engine designed to replicate and extend the WorldQuant Brain platform environment. ]It parses and evaluates Fast Expression Language (FEL) alpha signals locally against historical market data, providing researchers with sub-second iteration cycles and fully transparent performance metrics.

## 🚀 Core Objectives
* **Local FEL Execution:** Compile and execute raw FEL expressions into fully vectorized NumPy/Numba operations.
* **Transparent Metrics:** Reproduce Brain-style evaluation metrics including Sharpe, Fitness, Information Coefficient (IC), and Turnover.
* **Advanced Portfolio Logic:** Support single-alpha and multi-alpha portfolio modes with custom neutralization (Market/Sector/Industry), linear decay, and truncation.
* **High-Speed Iteration:** Process thousands of parameter variations in bulk using a highly optimized local data pipeline.

## 🏗️ System Architecture
[]The engine operates on a clean, multi-layered architecture:
1.**Data Infrastructure:** Ingests OHLCV and fundamentals into partitioned Parquet files, queried via DuckDB with Redis caching.
2. **FEL Expression Engine:** A 4-stage pipeline (Lexer -> Parser -> AST -> Evaluator) built with Lark that maps strings to array operations.
3.**Operator Library:** A comprehensive suite of cross-sectional and time-series operators (e.g., `ts_mean`, `rank`, `neutralize`) accelerated by Numba JIT.
4.**Backtesting Core:** Simulates daily P&L, applies trading costs, and enforces risk limits.
5. **REST API & UI:** A FastAPI backend serving a React/Vite dashboard for expression editing, visualization, and alpha management.

## 💻 Tech Stack
* **Core Numerics:** Python 3.11, NumPy, Numba, SciPy 
* **Data Layer:** Pandas, Polars, PyArrow, DuckDB, Redis 
* **Parser:** Lark 
* **API & Frontend:** FastAPI, React, Recharts, Monaco Editor 
