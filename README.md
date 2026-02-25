# 📊 Complete Data Visualization Guide (Matplotlib + Seaborn)
End-to-End README for Data Analysts  
(Covers Theory + Syntax + Interview + Templates)

---

# 1️⃣ Why Visualization is Important

• Helps in Exploratory Data Analysis (EDA)  
• Identifies patterns, trends, seasonality  
• Detects outliers  
• Validates assumptions  
• Communicates insights to stakeholders  

---

# 2️⃣ Installation & Setup

Install libraries:

pip install numpy pandas matplotlib seaborn

Import libraries:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_theme(style="whitegrid")  # clean default theme
```

---

# 3️⃣ How to Choose the Right Chart

Trend over time → Line plot  
Compare categories → Bar plot  
Distribution → Histogram / KDE  
Outliers → Box plot  
Spread comparison → Violin plot  
Relationship → Scatter plot  
Correlation → Heatmap  
Ranking → Sorted bar plot  

---

# 4️⃣ Matplotlib Fundamentals

Figure = Entire canvas  
Axes = Plot area  

Basic Plot:

```python
fig, ax = plt.subplots(figsize=(8,4))
ax.plot([1,2,3], [10,20,15])
ax.set(title="Basic Line Plot", xlabel="X Axis", ylabel="Y Axis")
ax.grid(True, alpha=0.3)
plt.show()
```

Multiple Subplots:

```python
fig, axes = plt.subplots(1,2, figsize=(12,4))

axes[0].plot([1,2,3], [10,20,15])
axes[0].set_title("Line Plot")

axes[1].hist([10,20,15,30,40], bins=5)
axes[1].set_title("Histogram")

plt.tight_layout()
plt.show()
```

---

# 5️⃣ Seaborn Fundamentals

Works best with Pandas DataFrame

```python
sns.lineplot(data=df, x="date", y="sales")
plt.show()
```

Using hue:

```python
sns.scatterplot(data=df, x="spend", y="sales", hue="segment")
plt.show()
```

---

# 6️⃣ Core Plots Every Data Analyst Must Know

📈 Line Plot (Trend)

```python
sns.lineplot(data=df, x="date", y="sales")
plt.xticks(rotation=45)
plt.title("Sales Trend")
plt.show()
```

📊 Bar Plot (Category Comparison)

```python
order = df.groupby("category")["sales"].sum().sort_values(ascending=False).index
sns.barplot(data=df, x="category", y="sales", estimator="sum", order=order)
plt.xticks(rotation=45)
plt.show()
```

📉 Histogram (Distribution)

```python
sns.histplot(df["income"], bins=30, kde=True)
plt.show()
```

📦 Box Plot (Quartiles + Outliers)

Box plot shows:
Q1 (25%), Median (50%), Q3 (75%)
IQR = Q3 - Q1
Outliers = 1.5 × IQR

```python
sns.boxplot(data=df, x="segment", y="income")
plt.show()
```

🎻 Violin Plot

```python
sns.violinplot(data=df, x="segment", y="income", inner="quartile")
plt.show()
```

🎯 Scatter Plot

```python
sns.scatterplot(data=df, x="marketing_spend", y="sales")
plt.show()
```

📈 Regression Plot

```python
sns.regplot(data=df, x="marketing_spend", y="sales")
plt.show()
```

🔥 Correlation Heatmap

```python
corr = df.select_dtypes(include="number").corr()
sns.heatmap(corr, annot=True, fmt=".2f", cmap="coolwarm")
plt.show()
```

🔍 Pairplot (Quick EDA)

```python
sns.pairplot(df.select_dtypes(include="number"))
plt.show()
```

---

# 7️⃣ Time Series Analysis

Convert to datetime:

```python
df["date"] = pd.to_datetime(df["date"])
df = df.sort_values("date")
```

Rolling average:

```python
df["ma7"] = df["sales"].rolling(7).mean()
sns.lineplot(data=df, x="date", y="sales")
sns.lineplot(data=df, x="date", y="ma7")
plt.show()
```

Monthly resampling:

```python
monthly = df.resample("M", on="date")["sales"].sum().reset_index()
sns.lineplot(data=monthly, x="date", y="sales")
plt.show()
```

---

# 8️⃣ Categorical Analysis

Count plot:

```python
sns.countplot(data=df, x="city")
plt.xticks(rotation=45)
plt.show()
```

Stacked bar:

```python
pivot = df.pivot_table(index="city", columns="segment", values="sales", aggfunc="sum", fill_value=0)
pivot.plot(kind="bar", stacked=True)
plt.show()
```

---

# 9️⃣ Advanced Styling

Add labels on bars:

```python
ax = sns.barplot(data=df, x="category", y="sales", estimator="sum")
for container in ax.containers:
    ax.bar_label(container)
plt.show()
```

Add target/reference line:

```python
sns.lineplot(data=df, x="date", y="sales")
plt.axhline(100000, linestyle="--")
plt.show()
```

Log scale:

```python
plt.xscale("log")
```

Save chart:

```python
plt.savefig("chart.png", dpi=300, bbox_inches="tight")
```

---

# 🔟 Common Mistakes

❌ No labels  
❌ No units  
❌ Too many colors  
❌ Not sorting categories  
❌ Using pie charts excessively  
❌ Truncated axes without explanation  

---

# 1️⃣1️⃣ Interview Theory (Important)

What does a box plot show?  
→ Median, Quartiles, IQR, Outliers  

Histogram vs KDE?  
→ Histogram = frequency bins  
→ KDE = smooth distribution curve  

Why use rolling average?  
→ To smooth noise & highlight trend  

When to use heatmap?  
→ To visualize correlation between numeric variables  

---

# 1️⃣2️⃣ Storytelling Framework

✔ What changed?  
✔ By how much?  
✔ Why did it change?  
✔ What action should be taken?  

---

# 1️⃣3️⃣ Professional Chart Template

```python
fig, ax = plt.subplots(figsize=(10,5))

sns.lineplot(data=df, x="date", y="sales", ax=ax)

ax.set(
    title="Monthly Sales Trend (2024)",
    xlabel="Date",
    ylabel="Sales ($)"
)

ax.grid(alpha=0.3)

plt.tight_layout()
plt.show()
```

---

# 🚀 Final Advice

• Keep visuals clean and simple  
• Always add labels and units  
• Sort categories  
• Focus on insights, not decoration  
• Explain business impact  

---

END OF COMPLETE DATA VISUALIZATION README
