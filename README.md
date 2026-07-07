# Plugging into the Future: An Exploration of Electricity Consumption Patterns

A Tableau data-analytics project exploring how India's state-wise electricity consumption changed from **January 2019 to December 2020** — a period spanning the COVID-19 pandemic and nationwide lockdown.

## Overview

Using daily state-level consumption records across **33 states** and **5 regions** (NR, SR, ER, WR, NER), this project builds an interactive Tableau dashboard and guided story to help energy analysts and policymakers explore three scenarios:

1. **Change in Overall Consumption Trends** — how national electricity usage shifted month-by-month from 2019 to 2020, including the impact of the lockdown.
2. **Regional Variations in Demand** — how consumption patterns differed across India's five regions due to climate, industrial presence, and population density.
3. **Recovery After Lockdown** — how quickly different states rebounded once lockdown restrictions eased, and which states lagged behind.

## Dataset

| Field | Description |
|---|---|
| `States` | Indian state or union territory |
| `Regions` | Grid region (NR, SR, ER, WR, NER) |
| `latitude` / `longitude` | Geographic coordinates of the state |
| `Dates` | Date of the recorded reading (Jan 2019 – Dec 2020) |
| `Usage` | Electricity consumption for that state and date (MU) |

- **Rows:** 16,599
- **Note:** 2020 has notably fewer reported rows per state than 2019 (avg. ~144 vs. ~359 days/state). Analyses in this project use **average daily usage** rather than raw yearly totals to avoid a reporting-frequency bias.

## Tech Stack

| Component | Technology |
|---|---|
| Data source | CSV (`Consumption.csv`) |
| Data preparation | Tableau Prep Builder |
| Visualization & dashboard | Tableau Desktop |
| Calculated fields | Tableau (lockdown-period flag, Top N / Bottom N rank) |
| Geocoding / mapping | Built-in Tableau geocoding + lat/long fields |
| Publishing | Tableau Public / Tableau Server |
| Web embedding | Tableau JavaScript API |
| Version control | GitHub |

## Dashboard & Story

The Tableau workbook includes:

- **Usage by Region** — bar chart of total usage by region, split by year (2019 vs. 2020)
- **Total Region Consumption** — pie chart of usage share by region
- **2019 / 2020 State Consumption** — choropleth/bubble maps of state-wise usage per year
- **Total Consumption** — dual bar chart comparing every state's usage across both years
- **Region Wise State Usage** — combined dashboard with Top N / Bottom N state rankings

## Key Calculated Fields

```
Top N Rank    = RANK(SUM([Usage]), 'desc')
Bottom N Rank = RANK(SUM([Usage]), 'asc')
Lockdown Flag = IF [Date] >= #2020-03-25# AND [Date] <= #2020-06-08#
                THEN "Lockdown"
                ELSEIF [Date] < #2020-03-25# THEN "Pre-Lockdown"
                ELSE "Post-Lockdown" END
```

## Project Structure

```
├── Consumption.csv                 # Source dataset
├── Plugging_into_the_Future.twbx   # Tableau packaged workbook
├── docs/
│   ├── Problem_Statements.docx
│   ├── Empathy_Map_Canvas.docx
│   ├── Brainstorm_Idea_Prioritization.docx
│   ├── Customer_Journey_Map.pdf
│   ├── Solution_Requirements.docx
│   ├── Data_Flow_Diagram_User_Stories.docx
│   ├── Technology_Stack.docx
│   ├── Problem_Solution_Fit.docx
│   ├── Proposed_Solution_Template.docx
│   ├── Solution_Architecture.docx
│   ├── Project_Planning_Template.docx
│   ├── Project_Performance_Test.docx
│   └── Final_Report.docx
└── README.md
```

## Team

| Name |
|---|
| Anshu Ojha |
| Lakshya Vardhan |
| Manoj Kumar |
| Dev Pareek |
| Bhanu Kandera |

## Project Planning

Work was organized into 4 sprints:

| Sprint | Focus | Story Points |
|---|---|---|
| Sprint-1 | Data Collection & Extraction, Data Preparation | 12 |
| Sprint-2 | Data Visualization, Dashboard, Story | 20 |
| Sprint-3 | Performance Testing, Web Integration | 13 |
| Sprint-4 | Project Demonstration & Documentation | 10 |

**Velocity:** 55 total points / 4 sprints = **13.8 story points per sprint**

## Links

- **Live Dashboard / Demo:** https://drive.google.com/drive/folders/1WomE8CdxmuzajJlKV8Frgk97AvVy7eWc?usp=sharing
- **GitHub Repository:** https://github.com/Arjunatwar/Plugging-into-the-Future.git
