# FX-Rate-Forecasting-Currency-Risk-Dashboard
Develop an FX forecasting and risk visualization tool that helps users understand currency trends, volatility, and potential high-risk periods for key FX pairs.

# Project Roadmap

# Project Roadmap

- **Phase 0 – Project Framing & Guardrails**
    
    **Objective**
    
    Build an FX analytics and forecasting system that:
    
    - Explains currency trends and volatility
    - Forecasts short-term FX movements
    - Flags potential high-risk periods
    - Is interpretable for individuals and small businesses
    
    **Key Design Decisions**
    
    - Forecast horizon: *short-term* (next day / next week)
    - Focus on **risk awareness**, not perfect prediction
    - Prefer **explainability + robustness** over complex black-box models
    
    **Deliverables**
    
    - Working FX analytics pipeline
    - Forecast comparison results
    - Interactive risk dashboard
    - Documentation for non-technical users
    
    **Tools**
    
    - Project tracking: Notion / Jira / GitHub Projects
    - Version control: Git + GitHub
- **Phase A – FX Pair Selection & Existing Data Audit**
    
    *(Subtask A  – FX Pair Selection & Existing Data Audit)*
    
    ### Goals
    
    - Identify FX pairs to include
    - Understand available historical coverage
    - Decide forecasting granularity and horizon
    
    ### Activities
    
    1. Select priority FX pairs
        - Core: USD/INR, EUR/INR
        - Reference: USD/EUR
    2. Audit Volunteer_Data_Collection FX datasets
        - Date range
        - Missing values
        - Frequency (daily preferred)
    3. Identify data gaps requiring API enrichment
    4. Lock forecasting horizon:
        - Day-ahead
        - 5-day / 7-day rolling forecast
    
    ### Deliverables
    
    - FX pair shortlist
    - Data quality audit report
    - Confirmed forecast horizon
    
    ### Tools
    
    - Python (Pandas)
    - Jupyter Notebook
    - Pandas profiling (`ydata-profiling`) or simple EDA notebooks
- **Phase B – FX Data Repository & Enrichment**
    
    *(Subtask B – depends on Phase A)*
    
    ### Goals
    
    Create a **single, clean FX master dataset** with derived analytics fields.
    
    ### Activities
    
    1. Merge Volunteer_Data_Collection FX data
    2. Fill gaps with **minimal API calls**
        - Open Exchange Rates (or equivalent)
    3. Standardize:
        - Date format
        - Currency pair naming
    4. Add derived fields:
        - Daily returns
        - Log returns
        - Rolling volatility (7, 14, 30 days)
        - Rolling averages
    
    ### Deliverables
    
    - Unified FX dataset (CSV / Parquet)
    - Reusable data ingestion scripts
    
    ### Tools
    
    - Python (Pandas, NumPy)
    - API access via `requests`
    - Storage:
        - Local CSV/Parquet (early)
        - Optional: PostgreSQL / SQLite for scalability
- **Phase C – Trend, Volatility & Correlation Analytics**
    
    *(Subtask C – depends on Phase B)*
    
    ### Goals
    
    Understand **how currencies behave historically** and identify risk regimes.
    
    ### Activities
    
    1. Trend analysis
        - Long-term vs short-term trends
    2. Volatility regime detection
        - Stable vs turbulent periods
    3. Correlation analysis
        - USD/INR vs EUR/INR
        - USD/EUR as global reference
    4. Identify historical stress periods
        - High volatility clusters
        - Sudden regime shifts
    
    ### Deliverables
    
    - Trend plots
    - Volatility bands
    - Correlation heatmaps
    - Analytical summary of findings
    
    ### Tools
    
    - Python (Pandas, NumPy)
    - Visualization:
        - Matplotlib / Seaborn
        - Plotly (for interactive charts)
- **Phase D – Baseline FX Forecasting Models**
    
    *(Subtask D – depends on Phase C)*
    
    ### Goals
    
    Establish **strong, explainable baseline models**.
    
    ### Activities
    
    1. Split data (train / validation / test)
    2. Build baseline models:
        - ARIMA / SARIMA
        - ETS (Exponential Smoothing)
        - Prophet
    3. Evaluate using:
        - MAE
        - RMSE
        - MAPE
    4. Generate rolling forecasts
    
    ### Deliverables
    
    - Baseline model forecasts
    - Error metric comparison table
    - Model assumptions documented
    
    ### Tools
    
    - Python
    - Libraries:
        - `statsmodels`
        - `prophet`
    - Experiment tracking:
        - MLflow (optional)
- **Phase E – Advanced FX Forecasting & Direction Accuracy**
    
    *(Subtask E – depends on Phase D)*
    
    ### Goals
    
    Improve **directional accuracy** and compare sophistication vs benefit.
    
    ### Activities
    
    1. Advanced models:
        - Tuned Prophet
        - LSTM / GRU (basic, not over-engineered)
    2. Feature enhancements:
        - Lagged returns
        - Volatility indicators
    3. Evaluate:
        - Forecast error
        - Direction accuracy (% correct up/down)
    4. Optional ensemble:
        - Average of classical + ML models
    
    ### Deliverables
    
    - Advanced model benchmarks
    - Direction accuracy comparison
    - Final model selection rationale
    
    ### Tools
    
    - Python
    - Deep learning:
        - TensorFlow / PyTorch
    - Experiment management:
        - MLflow / Weights & Biases (optional)
- **Phase F – Currency Risk & Forecast Dashboard**
    
    *(Subtask F – depends on Phase D)*
    
    ### Goals
    
    Make insights **visual, intuitive, and decision-oriented**.
    
    ### Dashboard Components
    
    - FX price trends
    - Volatility bands
    - Forecast overlays
    - Highlighted “high-risk” days
    - Historical context
    
    ### Tools (choose one primary)
    
    - **Streamlit** (best for Python-first projects)
    - Power BI / Tableau (if BI-oriented audience)
    
    ### Deliverables
    
    - Interactive FX dashboard
    - User-friendly layout for non-technical users
- **Phase G – Alert Logic & Historical Backtesting**
    
    *(Subtask G – depends on Phases E & F)*
    
    ### Goals
    
    Translate forecasts into **actionable risk signals**.
    
    ### Activities
    
    1. Define alert rules:
        - Forecasted move > X%
        - Volatility spike beyond threshold
    2. Backtest alerts on historical data
    3. Measure:
        - Frequency of alerts
        - False positives
        - Missed risk events
    4. Tune thresholds
    
    ### Deliverables
    
    - Alert rule definitions
    - Backtesting results
    - Recommended thresholds
    
    ### Tools
    
    - Python
    - Pandas
    - Visualization for alert timelines
- **Phase H – Documentation & Assumptions Summary**
    
    *(Subtask H – depends on all phases)*
    
    ### Goals
    
    Ensure **clarity, transparency, and usability**.
    
    ### Documentation Includes
    
    - Data sources & limitations
    - Model explanations (plain English)
    - Forecast interpretation guide
    - Risk disclaimer
    - “How to use this as a small business / individual”
    
    ### Deliverables
    
    - Technical documentation
    - User interpretation guide
    - Architecture diagram
    
    ### Tools
    
    - Markdown / Notion / Confluence
    - Diagrams:
        - Draw.io / Lucidchart

# **Execution Timeline**

# Week-by-Week Execution Timeline (8 Weeks)

Designed for 1 person or a small team, realistic pacing, no burnout.

- **Week 1 – Project Setup & Data Audit**
    
    **Milestone:** Clear scope + clean starting data
    
    **Tasks**
    
    - Finalize FX pairs (USD/INR, EUR/INR, USD/EUR)
    - Audit Volunteer_Data_Collection FX data
    - Decide forecast horizon (1-day & 7-day)
    - Set up repo + environment
    
    **Tools**
    
    - GitHub
    - Python, Pandas
    - Jupyter Notebook
    
    **Deliverables**
    
    - Data audit notebook
    - Project README (draft)
- **Week 2 – Data Enrichment & Feature Engineering**
    
    **Milestone:** Unified, analysis-ready FX dataset
    
    **Tasks**
    
    - Fill missing dates via Open Exchange Rates
    - Compute:
        - Returns & log returns
        - Rolling volatility (7/14/30)
    - Standardize FX schemas
    
    **Tools**
    
    - Python (Pandas, NumPy)
    - Requests (API calls)
    
    **Deliverables**
    
    - Master FX dataset (CSV/Parquet)
    - Data ingestion script
- **Week 3 – Trend, Volatility & Correlation Analysis**
    
    **Milestone:** Historical behavior understood
    
    **Tasks**
    
    - Trend decomposition
    - Volatility regime identification
    - Correlation heatmaps
    - Identify stress periods
    
    **Tools**
    
    - Matplotlib / Seaborn
    - Plotly (optional)
    
    **Deliverables**
    
    - EDA notebook
    - Analytical insights summary
- **Week 4 – Baseline Forecasting Models**
    
    **Milestone:** Reliable baseline forecasts
    
    **Tasks**
    
    - Train ARIMA / ETS / Prophet
    - Rolling window forecasting
    - Evaluate MAE, RMSE, MAPE
    
    **Tools**
    
    - statsmodels
    - Prophet
    
    **Deliverables**
    
    - Baseline model comparison
    - Forecast plots
- **Week 5 – Advanced Forecasting & Direction Accuracy**
    
    **Milestone:** Improved predictive insight
    
    **Tasks**
    
    - Train LSTM / GRU (simple)
    - Feature enhancements
    - Direction accuracy evaluation
    - Ensemble experimentation
    
    **Tools**
    
    - TensorFlow / PyTorch
    - MLflow (optional)
    
    **Deliverables**
    
    - Advanced model benchmark
    - Final model selection
- **Week 6 – FX Risk Dashboard**
    
    **Milestone:** Visual, decision-ready output
    
    **Tasks**
    
    - Build dashboard:
        - Trends
        - Volatility bands
        - Forecasts
    - Highlight high-risk days
    
    **Tools**
    
    - Streamlit (recommended)
    - Plotly
    
    **Deliverables**
    
    - Interactive dashboard
    - Deployed app (optional)
- **Week 7 – Alert Logic & Backtesting**
    
    **Milestone:** Actionable risk signals
    
    **Tasks**
    
    - Define alert thresholds
    - Backtest on history
    - Tune false positives
    
    **Tools**
    
    - Pandas
    - Visualization tools
    
    **Deliverables**
    
    - Alert performance report
    - Final alert rules
- **Week 8 – Documentation & Polish**
    
    **Milestone:** Interview-ready project
    
    **Tasks**
    
    - Write documentation
    - Create diagrams
    - Final README
    
    **Tools**
    
    - Markdown
    - Draw.io / Lucidchart
    
    **Deliverables**
    
    - Complete documentation
    - Portfolio-ready project

# System Architecture Diagram (Text + Explanation)

**High-Level Architecture**

FX Data Sources
├── Volunteer_Data_Collection
├── Open Exchange Rates API
└── Public FX Datasets
↓
Data Ingestion Layer
├── Data cleaning
├── Gap filling
└── Feature engineering
↓
Analytics Layer
├── Trend analysis
├── Volatility modeling
├── Correlation analysis
↓
Forecasting Layer
├── Baseline models (ARIMA, ETS, Prophet)
├── Advanced models (LSTM / GRU)
└── Ensemble forecasts
↓
Risk & Alert Engine
├── Volatility thresholds
├── Forecasted move alerts
└── Backtesting logic
↓
Visualization Layer
└── Interactive FX Dashboard (Streamlit)

### **Why This Design Works**

- **Modular** → models can be swapped without breaking the system
- **Explainable** → analytics first, ML second
- **Scalable** → new FX pairs easily added
- **User-centric** → risk signals, not raw predictions
