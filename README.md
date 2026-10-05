# Ticket Analytics Dashboard

SQL and Excel analysis of IT support tickets: which problems happen most, how long they take to resolve, when requests peak, and what the IT team should do about it.

**Status:** [In progress / Completed] | **Portfolio:** https://github.com/Warden64595/project-personal-portfolio

## 1. Project Overview
This project analyzes IT support tickets with SQL and Excel (or Google Sheets). It turns raw ticket records into clear charts, a dashboard, and written recommendations that help an IT team plan its work.

## 2. Problem Statement
IT teams receive many tickets but rarely study the pattern. Without analysis, repeat problems stay unfixed and staff are not scheduled for the busiest days.

## 3. Objectives
1. Clean and organize the ticket data.
2. Answer four questions with SQL: what happens most, how long it takes to fix, when requests peak, and who handles them.
3. Build charts and a dashboard in Excel or Google Sheets.
4. Write findings and recommendations based on the results.

## 4. Target Users
| User | How they use the results |
|---|---|
| IT manager | Plans staffing and priorities |
| Help desk technicians | Finds and fixes repeat problems |

## 5. Data Source
[State clearly where the data comes from: real tickets with all names and personal details removed, or sample data you created. Label sample data as **sample**.]

> **Privacy note:** Do not upload real company data without permission. Remove names, employee IDs and any confidential details first, or use sample data.

## 6. Tools Used
| Purpose | Tool |
|---|---|
| Database and queries | SQL (MySQL) |
| Cleaning, pivot tables, charts, dashboard | Excel or Google Sheets |
| Version control | Git and GitHub |
| Optional extras | [Python, Pandas, Matplotlib or Power BI] |

## 7. Deliverables
- [ ] Cleaned dataset
- [ ] SQL queries file
- [ ] Charts
- [ ] Dashboard
- [ ] Findings and recommendations
- [ ] This README
(Tick only what is finished.)

## 8. Repository Structure
```
ticket-analytics-dashboard/
├── README.md
├── data/        tickets.csv, categories.csv, technicians.csv
├── sql/         schema.sql, queries.sql
├── dashboard/   dashboard.xlsx
└── docs/        erd.png, dashboard.png, chart images
```

## 9. Data Dictionary
| Column | Type | Meaning |
|---|---|---|
| ticket_id (PK) | Number | Unique ticket number |
| created_at | Date and time | When the ticket was opened |
| closed_at | Date and time | When it was resolved (empty if still open) |
| category_id (FK) | Number | Links to categories (Network, Hardware, Software, Account, Printer) |
| priority | Text | Low, Medium or High |
| status | Text | Open, In progress or Closed |
| department | Text | Who reported the problem |
| technician_id (FK) | Number | Links to technicians |

## 10. Database Design
![ERD](docs/erd.png)

```sql
CREATE TABLE categories  (id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(50) NOT NULL);
CREATE TABLE technicians (id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(80) NOT NULL);
CREATE TABLE tickets (
  ticket_id     INT PRIMARY KEY,
  created_at    DATETIME NOT NULL,
  closed_at     DATETIME NULL,
  category_id   INT NOT NULL,
  priority      ENUM('Low','Medium','High') NOT NULL,
  status        ENUM('Open','In progress','Closed') NOT NULL,
  department    VARCHAR(60),
  technician_id INT,
  FOREIGN KEY (category_id)   REFERENCES categories(id),
  FOREIGN KEY (technician_id) REFERENCES technicians(id)
);
```

## 11. Data Cleaning
Tick each step when you have done it:
- [ ] Remove duplicate rows.
- [ ] Leave `closed_at` empty for tickets that are still open.
- [ ] Standardize category names (for example "wifi" and "Wi-Fi" become Network).
- [ ] Check that `closed_at` is after `created_at`.
- [ ] Convert text dates into real date values.

## 12. SQL Queries
All queries are in `sql/queries.sql`.

| # | Question | Result used for |
|---|---|---|
| 1 | Tickets per category | Bar chart |
| 2 | Average hours to resolve, per category | Bar chart |
| 3 | Tickets per weekday | Bar chart |
| 4 | Tickets per day | Line chart |
| 5 | Repeat problems | Findings |
| 6 | Technician workload | Findings |

Example:
```sql
SELECT c.name AS category, COUNT(*) AS total
FROM tickets t JOIN categories c ON t.category_id = c.id
GROUP BY c.name ORDER BY total DESC;
```

## 13. Dashboard and Charts
![Dashboard](docs/dashboard.png)

| Tickets per category | Average resolution time | Tickets per weekday |
|---|---|---|
| ![](docs/chart-category.png) | ![](docs/chart-resolution.png) | ![](docs/chart-weekday.png) |

## 14. Findings and Recommendations
**Findings:** [1 to 2 paragraphs in your own words, using your real numbers.]

**Recommendations:** [What the IT team should do because of these findings.]

## 15. How to Reproduce
```bash
git clone https://github.com/Warden64595/ticket-analytics-dashboard.git
cd ticket-analytics-dashboard
```
1. In MySQL, create the database: `CREATE DATABASE ticket_analytics;`
2. Run `sql/schema.sql`, then import the three CSV files from `data/` into their tables.
3. Run `sql/queries.sql` and export each result.
4. Open `dashboard/dashboard.xlsx`. The pivot tables and charts use those results.

## 16. Testing and Data Quality Checks
| Check | How I check it | Result |
|---|---|---|
| Row count matches the source file | Compare counts in SQL and in the original file | [Pass/Fail] |
| No duplicate ticket_id | `GROUP BY ticket_id HAVING COUNT(*) > 1` | [Pass/Fail] |
| No ticket closed before it was created | Query where `closed_at < created_at` | [Pass/Fail] |
| SQL totals match Excel pivot totals | Compare each chart total with a pivot table | [Pass/Fail] |
| Category names are consistent | List the distinct category values | [Pass/Fail] |

## 17. Limitations
[Example: small dataset, only one month of data, categories assigned by hand.]

## 18. Future Improvements
[Example: more months of data, a Power BI or Python version, automatic data import.]

## 19. Use of AI Tools
AI tools helped me plan the project and draft the SQL queries and documentation. [Describe what you personally checked: for example, ran each query on your own tables, compared the results with Excel pivot tables, and fixed any errors.] See the AI usage log in my portfolio.

## 20. Developer
**Edward S. Vidal**, BSIT, Datamex College of Saint Adeline
GitHub: https://github.com/Warden64595 | LinkedIn: https://www.linkedin.com/in/edward-vidal-5536613a5 | Email: edwardsajovidal@gmail.com
