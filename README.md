# HR Analytics Dashboard (Power BI)

An interactive four-page Power BI report that analyses a workforce across headcount, demographics, performance, and attrition. It helps HR teams see who works in the organisation, how employees rate their experience, and which factors are linked to people leaving.

![Overview page](screenshots/01_overview.png)

---

## Table of Contents
- [Business Questions](#business-questions)
- [Report Pages](#report-pages)
- [Data Model](#data-model)
- [DAX Measures](#dax-measures)
- [Design](#design)
- [Key Insights](#key-insights)
- [How to Open the Report](#how-to-open-the-report)
- [Repository Structure](#repository-structure)
- [Data Source and Credits](#data-source-and-credits)
- [License](#license)

---

## Business Questions

- How many employees does the company have, how many are active, and what is the attrition rate?
- How has hiring changed over time, and which departments and job roles are the largest?
- What does the workforce look like by age, gender, marital status and ethnicity?
- How do individual employees rate their job, environment, work-life balance and relationships over time?
- Which factors (department, job role, business travel, overtime, tenure) are associated with higher attrition?

---

## Report Pages

The report has **four pages** (1280 × 720) with a page navigator on each for easy movement.

### 1. Overview
- KPI cards: **Total Employees**, **Active Employees**, **Inactive Employees**, **% Attrition Rate**
- **Employee Hiring Trends**: column chart over a Year > Quarter > Month > Day hierarchy, split by attrition status
- **Active Employees by Department**: clustered bar chart
- **Active Employees by Department and Job Role**: treemap

### 2. Demographics
- Cards: **Youngest Employee** and **Oldest Employee**
- **Employees by Age**: column chart by age bins
- **Employees by Age and Gender**: 100% stacked column chart
- **Employees by Marital Status**: donut chart
- **Employees by Ethnicity and Average Salary**: combo (column + line) chart

### 3. Performance Tracker
- An **employee name slicer** to drill into one person
- Cards: **Start Date**, **Last Review**, **Next Review**
- Six line charts by year: **Job Satisfaction**, **Relationship Satisfaction**, **Self Rating**, **Work Life Balance**, **Manager Rating**, **Environment Satisfaction**
- Reference tables explaining the rating levels and satisfaction levels

### 4. Attrition
- **% Attrition Rate** card
- Attrition by **Department and Job Role**
- **Attrition by Hire Date** (Year > Quarter > Month > Day)
- **Attrition by Travel Frequency** (with headcount as a second axis)
- **Attrition by Overtime Requirement**
- **Attrition by Tenure** (years at company)

---

## Data Model

The model follows a **star schema**: one fact table surrounded by dimension tables, plus a dedicated table for measures.

| Table | Role |
|-------|------|
| `FactPerformanceRating` | Fact table holding employee review/rating records |
| `DimEmployee` | Employee attributes (department, job role, age, gender, marital status, ethnicity, hire date, overtime, business travel, years at company, attrition) |
| `DimDate` | Date table with a Year / Quarter / Month / Day hierarchy |
| `DimRatingLevel` | Lookup for rating levels |
| `DimSatisfiedLevel` | Lookup for satisfaction levels |
| `DimEducationLevel` | Lookup for education levels |
| `_Measures` | Table that stores all DAX measures |

`[Optional: add a screenshot of the Model view as screenshots/model_view.png and embed it here.]`

---

## DAX Measures

All measures live in the `_Measures` table.

| Measure | Purpose |
|---------|---------|
| `TotalEmployees` | Total headcount |
| `ActiveEmployees` | Employees who have not left |
| `InactiveEmployees` | Employees who have left |
| `% Attrition Rate` | Share of employees who left |
| `TotalEmployeesDate` | Headcount for the date-based hiring trend |
| `% Attrition Rate Date` | Attrition rate for the date-based trend |
| `AverageSalary` | Average salary (used on the Demographics page) |
| `LastReviewDate` / `NextReviewDate` | Most recent and upcoming review for the selected employee |
| `JobSatisfaction`, `RelationshipSatisfaction`, `EnvironmentSatisfaction`, `WorkLifeBalance`, `SelfRating`, `ManagerRating` | Average rating scores over time |

`[Optionally paste the DAX for your key measures, for example % Attrition Rate, in a code block here.]`

---

## Design

- **Custom theme:** a custom *HR Analytics* theme built on the Power BI `CY21SU11` base theme.
- **Palette:** `#03EF62` (green), `#05192D` (navy), `#06BDFC` (blue), `#FF5400` (orange), `#FF931E`, `#7933FF`, `#FF6EA9`, `#FCCE0D`.
- **Typography:** Segoe UI Semibold for titles and callout numbers.
- **Navigation:** A page navigator on every page.

---

## Key Insights

`[Fill these in from your dashboard. Use real numbers. Examples of the format:]`

- Overall attrition rate is `[X%]`, with `[N]` active and `[N]` inactive employees.
- `[Department / job role]` has the highest attrition at `[X%]`.
- Employees who work overtime leave at `[X%]` versus `[Y%]` for those who do not.
- Attrition is highest in the first `[N]` years of tenure.
- `[Observation about demographics or satisfaction trends]`

---

## How to Open the Report

1. Install **Power BI Desktop** (free, Windows): https://powerbi.microsoft.com/desktop/
2. Download [`report/HR_Analytics_Dashboard.pbix`](report/HR_Analytics_Dashboard.pbix) from this repository (open the file page and click the download icon).
3. Double-click the file to open it in Power BI Desktop.

GitHub cannot preview `.pbix` files, so use the screenshots in this README to see the dashboard without installing anything.

---

## Repository Structure

```
.
├── README.md
├── HR_Analytics_Dashboard.pbix
└── screenshots/
    ├── 01_overview.png
    ├── 02_demographics.png
    ├── 03_performance_tracker.png
    └── 04_attrition.png
```

---

## Data Source and Credits

- **Dataset:** `[Data was provided by Datacamp platform for the project]`. Data is imported into the `.pbix` file.
- **Course / tutorial:** `[This report was created during learning of powerbi course in datacamp]`

---

## License

`[MIT]`. See `LICENSE`. The dataset remains subject to its original license.
