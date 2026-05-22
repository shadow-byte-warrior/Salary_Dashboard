# 📊 Excel Salary Dashboard

![Dashboard Preview](https://github.com/user-attachments/assets/de814eca-c1c7-4590-b94c-86a08d1309bf)

> An interactive Excel dashboard for exploring data science job salaries by title, location, and schedule type — built to help job seekers make informed career decisions.

---

## 📌 Overview

This **Data Jobs Salary Dashboard** was built to help job seekers investigate salaries for their desired roles and benchmark whether they're being fairly compensated. The dataset contains real-world data science job information from **2023**, covering job titles, salaries, locations, and required skills.

🔗 **Dashboard File:** [`1_Salary_Dashboard.xlsx`](1_Salary_Dashboard.xlsx)

---

## 🛠️ Excel Skills Used

| Skill | Purpose |
|---|---|
| 📉 Charts | Bar chart & map chart for visual salary comparison |
| 🧮 Formulas & Functions | `MEDIAN()`, `IF()`, `FILTER()` for dynamic salary calculation |
| ❎ Data Validation | Dropdown filters for job title, country, and schedule type |

---

## 📂 Dataset

The dataset includes real-world data science job postings from 2023 with:

- 👨‍💼 **Job Titles** — e.g., Data Analyst, Data Scientist, ML Engineer
- 💰 **Salaries** — Annual averages in USD
- 📍 **Locations** — Country-level breakdown
- 🛠️ **Skills** — Required tools and technologies per role

---

## 🏗️ Dashboard Build

### 📊 Chart 1 — Data Science Job Salaries (Bar Chart)

<img src="/0_Resources/Images/1_Salary_Dashboard_Chart1.png" width="850" height="550" alt="Salary Bar Chart">

**What was built:**
- Horizontal bar chart comparing **median annual salaries** across job titles
- Sorted in descending order for quick visual scanning

**Key Insight:**
> Senior roles and Engineering positions consistently earn more than Analyst roles — useful for planning career progression.

---

### 🗺️ Chart 2 — Country Median Salaries (Map Chart)

![Country Map](./0_Resources/Images/1_Salary_Dashboard_Country_Map.gif)

**What was built:**
- A **color-coded geographic map** showing median salaries by country
- Immediately communicates global salary disparities at a glance

**Key Insight:**
> The map highlights high-paying regions (North America, Western Europe) vs lower-paying regions — critical for remote job seekers evaluating location-based offers.

---

### 🧮 Formulas & Functions

#### 💰 Median Salary by Job Title, Country & Type

```excel
=MEDIAN(
  IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
  )
)
```

| Feature | Description |
|---|---|
| 🔍 Multi-Criteria Filter | Filters by job title, country, schedule type, and excludes blank salaries |
| 📊 Array Formula | Uses `MEDIAN()` with nested `IF()` across an array of data |
| 🎯 Dynamic Output | Automatically updates based on dropdown selections in the dashboard |

📸 Background Table:

<img width="1864" height="636" alt="Screenshot 2026-05-22 112857" src="https://github.com/user-attachments/assets/a25e3d8f-53cc-4637-82c5-d1f626655758" />


📉 Dashboard Implementation:

<img src="/0_Resources/Images/1_Salary_Dashboard_Job_Title.png" width="400" height="500" alt="Job Title Filter">

---

#### ⏰ Count of Job Schedule Type

```excel
=FILTER(J2#,(NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#))))*(J2#<>0))
```

| Feature | Description |
|---|---|
| 🔍 Unique List | Filters out combined/multi-type entries (e.g., "Full-time and Part-time") |
| 🚫 Zero Exclusion | Omits blank or zero values from the schedule type list |
| 📋 Clean Output | Returns a clean, unique list of valid schedule types for dropdown use |

📸 Background Table:

![Screenshot2](/0_Resources/Images/1_Salary_Dashboard_Screenshot2.png)

📉 Dashboard Implementation:

<img src="/0_Resources/Images/1_Salary_Dashboard_Type.png" width="350" height="500" alt="Schedule Type Filter">

---

### ❎ Data Validation

To ensure accurate, consistent user input across the dashboard:

- **Job Title**, **Country**, and **Schedule Type** all use validated dropdown lists
- Inputs are restricted to predefined, filtered options — preventing incorrect entries
- Enhances usability and ensures the `MEDIAN()` formula always receives valid filter values

![Data Validation GIF](/0_Resources/Images/1_Salary_Dashboard_Data_Validation.gif)

---

## 💡 Key Insights

- 📈 **Senior roles and Engineers** earn significantly more than Analyst roles
- 🌍 **Geography matters** — the same role can have vastly different salaries depending on country
- ⏰ **Schedule type** (Full-time vs Part-time vs Contract) noticeably affects salary medians
- 🧮 **Array formulas** in Excel can replicate dynamic filtering without Power Query or macros

---

## 🚀 How to Use

1. Download [`1_Salary_Dashboard.xlsx`](1_Salary_Dashboard.xlsx)
2. Open in **Microsoft Excel** (2019 or later recommended for `FILTER()` support)
3. Use the **dropdown menus** to filter by:
   - Job Title
   - Country
   - Schedule Type
4. The charts and salary figures update automatically

---

## 👤 Author

**Arun Pandian**  
AI & Data Science Graduate | Aspiring Data Analyst  
📍 Coimbatore, Tamil Nadu  
🔗 [LinkedIn](https://linkedin.com/in/your-link) • [GitHub](https://github.com/shadow-byte-warrior)

---

## 📄 License

This project is open for educational and portfolio use. Dataset sourced from a structured Excel course on real-world data science job postings (2023).
