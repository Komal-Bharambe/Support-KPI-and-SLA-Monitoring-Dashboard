# Support Incidents Analytics Dashboard (Power BI)

## 📌 Project Overview
This Power BI project analyzes Support Operations performance across **volume, speed, quality, and risk**.  
It uses 5 CSV datasets to model relationships, calculate KPIs with DAX, and deliver insights that help Support Leaders improve service performance, staffing decisions, and customer experience.

---

## 📁 Dataset Information
The dashboard uses the following input files:

### 1. support_customers.csv  
- CustomerID  
- Name  
- Region  
- Industry  
- ContractTier  

### 2. support_agents.csv  
- AgentID  
- Name  
- Team  
- Location  

### 3. support_sla_plans.csv  
- SLAPlan  
- Priority  
- FirstResponseTargetMinutes  
- ResolutionTargetHours  

### 4. support_incidents.csv  
- IncidentID  
- CustomerID  
- AgentID  
- Channel  
- Category/Subcategory  
- Priority  
- Status  
- FirstResponseMinutes  
- ResolutionHours  
- FirstResponseBreach  
- ResolutionBreach  
- Reopened  
- Escalated  
- CSAT  
- CreatedAt / ClosedAt timestamps  

### 5. support_interactions.csv  
- InteractionID  
- IncidentID  
- Timestamp  
- Actor (Customer/Agent/System)  
- Type (Note, Update, Email, Call, etc.)  
- AgentID  

---

## 🧩 Data Model Architecture

### 🔹 Star Schema
- **Fact Table**: support_incidents  
- **Dimension Tables**: customers, agents, sla_plans, interactions, date table  
- Relationships follow:
  - **1-to-many** from dimensions → fact  
  - **Single-direction** filters (downstream only)  

---

## 📊 Key KPIs (DAX Measures)

### 1️⃣ New Incidents  
- By day/week/month  
- Compare vs previous period using `DATEADD`

### 2️⃣ SLA Performance  
- % First Response SLA Met  
- % Resolution SLA Met  
- Using SLA targets from `support_sla_plans`

### 3️⃣ Response/Resolution Speed  
- Median First Response Minutes  
- Median Resolution Hours  

### 4️⃣ Backlog & Aging  
- Backlog = Open + Pending + In Progress + On Hold  
- Tickets aged > 7, 14, 30 days  

### 5️⃣ Risk Indicators  
- Escalation Rate  
- Reopen Rate  

### 6️⃣ Customer Satisfaction (CSAT)  
- Average CSAT for Resolved/Closed tickets  
- Exclude blanks  

---

## 🖥️ Dashboard Sections

### **1. Volume Overview**
- New Incidents trend (line chart)  
- Incident volume by Channel, Priority, Category  

### **2. SLA Compliance**
- SLA Met % by Priority / Plan / Channel  
- SLA breaches heatmap  

### **3. Speed (Response & Resolution)**
- Median response/resolution times  
- Month-over-month trends  

### **4. Backlog & Aging**
- Current backlog count  
- Tickets aged > 7/14/30 days (bar chart)  

### **5. Quality & Risk**
- Escalation Rate  
- Reopen Rate  
- Agent-level performance  

### **6. CSAT Insights**
- Average CSAT  
- CSAT distribution  
- CSAT by Region, Tier, or Priority  

---

## 📌 Business Questions Answered

- **Where are we missing SLAs the most?**  
  (By Priority, Plan, Channel, Category)

- **Which customer cohorts drive the most volume and breaches?**  
  (Region, Industry, Tier)

- **Where are escalations or reopens concentrated?**  
  (Category or Agent level)

- **How do response & resolution times trend over months?**  
  (Identify seasonality or spikes)

- **What actions can improve the next sprint?**  
  (Staffing, training, process improvements)

---

## ⚙️ Data Quality Handling

- CSAT blanks excluded from averages  
- Missing First Response timestamps handled with conditional DAX  
- SLA breaches recalculated using SLA Plan targets (don’t rely only on input flags)  

---

## 🏁 Outcome
This dashboard delivers a complete operational view of Support performance—helping leadership track workload, SLA risks, customer satisfaction, and agent efficiencies.

It can be extended to:
- forecast volume,  
- identify root causes, and  
- recommend staffing improvements.

---

## 📂 Tools Used
- **Power BI**  
- **DAX**  
- **Power Query**  
- **Data Modeling (Star Schema)**  
- **CSV data**  



