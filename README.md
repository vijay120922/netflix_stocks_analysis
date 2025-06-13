
#  Netflix Stock Data Analysis (NFLX.csv)

This project analyzes Netflix's historical stock data using Python and popular data science libraries. It provides visual insights and key metrics like volume trends and highest/lowest stock prices over time.

---

## 📌 Objectives

- 📊 Analyze volume of stock traded
- 📉 Plot stock prices: High, Open, and Close over time
- 📆 Breakdown stock data by day, month, and year
- 🏆 Identify top 5 dates with the **highest** stock price
- 📉 Identify top 5 dates with the **lowest** stock price

---

## 🛠 Technologies Used

- **Python** (pandas, numpy)
- **Jupyter Notebook**
- **Matplotlib**
- **Seaborn**

---

## 📂 Dataset

- File: `NFLX.csv`
- Contains columns like: `Date`, `Open`, `High`, `Low`, `Close`, `Volume`

---

## 🧠 Key Code & Analysis

### 📅 Convert and Index Dates

```python
df['Date'] = pd.to_datetime(df['Date'])
df = df.set_index('Date')
```

### 📈 Volume Traded Over Time

```python
sns.lineplot(x=df.index, y=df['Volume'], label="Volume")
plt.title("Stock Volume Over Time")
```

### 📉 Plot Stock Prices: High, Open, Close

```python
df.plot(y=['High', 'Open', 'Close'], title='Netflix Stock Prices')
```

### 🗓️ Average Volume by Day, Month, Year

```python
fig, (ax1, ax2, ax3) = plt.subplots(3, figsize=(25,15))
df.groupby(df.index.day).mean().plot(y='Volume', ax=ax1, xlabel='Day')
df.groupby(df.index.month).mean().plot(y='Volume', ax=ax2, xlabel='Month', color='red')
df.groupby(df.index.year).mean().plot(y='Volume', ax=ax3, xlabel='Year', color='green')
```

### 🏆 Top 5 Dates with Highest Stock Price

```python
highest = df.sort_values(by='High', ascending=False).head(5)
print(highest['High'])
```

### 📉 Top 5 Dates with Lowest Stock Price

```python
lowest = df.sort_values(by='Low', ascending=True).head(5)
print(lowest['Low'])
```

---

## 📸 Sample Visuals

- Line plot of stock volume vs time  
- Line chart comparing High, Open, Close prices  
- Multi-subplot for daily, monthly, yearly volume trends  

---

## 🚀 How to Run

1. Clone this repo:
   ```bash
   git clone https://github.com/your-username/netflix-stock-analysis.git
   cd netflix-stock-analysis
   ```

2. Install requirements (optional if using Colab):
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```

3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

---

## 📌 License

This project is for educational purposes.

---
