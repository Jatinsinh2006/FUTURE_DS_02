# FUTURE_DS_02
# Customer Churn Analysis Using Accounts, Subscription & Feature Usage Data
## 📊 Customer Churn Analysis Dashboard

**Created By:** Jatinsinh Solanki  
**Tool:** Power BI Desktop  
**Dataset:** RavenStack Customer Data (Accounts, Subscriptions, Usage, Churn, Support)

---

## 🎯 Project Purpose

This Power BI dashboard analyzes customer churn trends and identifies why customers leave, which customer groups churn the most, and how churn affects revenue, product usage, and support performance.

---

## 🛠 Tools Used

- Power BI Desktop  
- Power Query Editor  
- DAX (Data Analysis Expressions)  

---

## 📂 Dataset Overview

This project uses **5 datasets**:

### **1. ravenstack_accounts**
- account_id  
- country  
- industry  
- plan_tier  
- is_trial  
- signup_date  

### **2. ravenstack_subscriptions**
- mrr_amount  
- arr_amount  
- auto_renew_flag  
- upgrade_flag  
- downgrade_flag  
- start_date / end_date  

### **3. ravenstack_churn_events**
- churn_date  
- reason_code  
- refund_amount_usd  

### **4. ravenstack_feature_usage**
- usage_count  
- usage_duration  
- error_count  
- feature_name  

### **5. ravenstack_support_tickets**
- priority  
- escalation_flag  
- resolution_time  
- satisfaction_score  

---

## 🧹 Data Cleaning

I performed the following tasks:

1. Corrected column name typos  
2. Converted date fields to date format  
3. Converted churn flags & trial flags to numeric values  
4. Removed duplicates  
5. Standardized country, industry, and plan tier values  
6. Created relationships between all tables  

---

## 📏 Key Metrics (DAX)

### Total Customers
```DAX
Total Customers = COUNT(accounts[account_id])
```

### Total Churn
```DAX
Total Churn = COUNT(churn_events[account_id])
```

### Churn Rate
```DAX
Churn Rate = DIVIDE([Total Churn], [Total Customers])
```

### Active Customers
```DAX
Active Customers = [Total Customers] - [Total Churn]
```

### Monthly Churn
```DAX
Monthly Churn = COUNT(churn_events[account_id])
```

### Monthly Active Customers
```DAX
Monthly Active Customers = [Total Customers] - [Monthly Churn]
```

### Cumulative Churn
```DAX
Cumulative Churn =
CALCULATE(
    [Total Churn],
    FILTER(
        ALL(churn_events[churn_date]),
        churn_events[churn_date] <= MAX(churn_events[churn_date])
    )
)
```

---

## 📊 Dashboard Features

### **Visuals Included:**
- KPI Cards (Total Customers, Total Churn, Churn Rate, Active Customers, ARR)
- Pie Chart: Churn by Plan Tier  
- Pie Chart: Churn by Country  
- Stacked Area Chart: Monthly churn trend  
- Decomposition Tree (trial users → country → industry → churn)  
- Ribbon Chart: Count of account by Month & plan tier  
- Bar Chart: Support ticket churn rate  
- Line Chart: MRR Trend by day  
- Area Chart: Active Customers vs Total Churn  

### **Filters Added:**
- Month  
- Plan Tier  
- Country  

---

## 🔍 Key Insights

Based on my analysis:

✅ US shows the highest churn rate  
✅ Pro plan users contribute the most churn  
✅ Trial users show significantly high churn  
✅ High-priority support tickets correlate with more churn  
✅ Monthly churn remains high throughout the year  
✅ Low feature usage leads to higher churn  

---

## 🎓 Skills Demonstrated

- Power BI Data Modeling  
- Data Transformation in Power Query  
- DAX Calculations  
- KPI Design & Dashboard Formatting  
- Analytical Storytelling  
- Customer Behavior Analysis  

---

## 🌟 Support

⭐ If this project helped you, please star the repository!  

---

**Built by Jatinsinh Solanki** 📊  
