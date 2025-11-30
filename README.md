# Market Anomaly Detection Engine (Microsoft Stock)
### *Detecting suspicious trading activity using ML + financial time-series signals*

This project builds an **anomaly detection system** that flags unusual trading behavior in Microsoft (MSFT) stock using **Yahoo Finance data**, **feature engineering**, and **Isolation Forest machine learning**.  
It blends **fintech analytics**, **AI-security principles**, and **quant-style time-series modeling**.

---

## 🚀 Project Overview

Financial markets experience sudden spikes, crashes, volatility shocks, and volume surges. Many are news-driven — but some represent **information imbalance, manipulation, or abnormal trading behavior**.

This project automatically detects those **outlier events**.

### ✔️ Uses Yahoo Finance OHLCV data  
### ✔️ Engineers anomaly-sensitive financial features  
### ✔️ Trains an Isolation Forest model to detect unusual days  
### ✔️ Visualizes anomalies directly on the price chart  
### ✔️ Outputs “Top 10 Most Suspicious Days” automatically  

Perfect for fintech, quant research, or AI-security portfolio work.

---

## 🧠 Why This Project Matters

Traditional time-series models assume markets behave normally.

But in real life:

- insider info leaks  
- coordinated buying/selling  
- algorithmic misfires  
- false news events  
- bot-driven sentiment cycles  
- manipulation attempts  

…all cause behavior that **breaks normal patterns**.

This ML pipeline identifies these breaks.

---

# 🔍 How It Works

## 1️⃣ Data Collection

Using `yfinance`, we pull daily OHLCV data:

- Open  
- High  
- Low  
- Close  
- Adjusted Close  
- Volume  

---

## 2️⃣ Feature Engineering

We engineer features that capture “market weirdness”:

| Feature | Meaning | Why it helps detect anomalies |
|--------|---------|-------------------------------|
| **return** | daily % price change | detects abrupt spikes/drops |
| **volatility_10** | rolling volatility | flags turbulent regimes |
| **volume_z** | z-score of volume vs 20-day history | detects accumulation/dump patterns |
| **intraday_range** | (high–low)/close | highlights chaotic trading days |
| **gap_open** | open vs previous close | detects suspicious overnight moves |

These features create a **behavioral signature** for each trading day.

---

## 3️⃣ Normalization

We standardize all features so the anomaly detector treats them equally:

```python
X = (features - mean) / std
```

4️⃣ Anomaly Detection (Isolation Forest)

We apply a tree-based anomaly detection model:

- learns normal stock behavior

- isolates points that behave unusually

- outputs anomaly scores + labels

Where:

- 1 = normal
- -1 = anomaly
- lower score = more suspicious

--

5️⃣ Visualization

We plot:

the stock price

red scatter points for anomaly days

This creates a clear, intuitive view of abnormal market behavior.

--

📈 Example Output
Top 10 Suspicious Days include patterns like:

- unusual volume spikes

- sharp downward movements

- large intraday swings

- unexpected pre-market gaps

- volatility regime shifts

🛠️ Tech Stack

- Python 3

- yfinance

- pandas / numpy

- scikit-learn (Isolation Forest)

- matplotlib

Optional enhancements:

- HuggingFace transformers (news sentiment)

- Streamlit (interactive dashboard)

Future Enhancements: 

⭐ News + Sentiment Integration

- Pull Yahoo Finance headlines & compute sentiment to enhance anomaly explanation.

⭐ Explanation Layer

- Add natural-language reasons for each anomaly:

- “High volume spike + negative return → potential dump pattern.”

⭐ Streamlit Web App

Interactive dashboard with:

- ticker dropdown

- anomaly heatmaps

- sentiment charts

⭐ Clustering

- Categorize anomalies into groups like “volatility shock,” “gap anomaly,” etc.
