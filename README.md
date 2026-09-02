<p align="center">
  <img src="images/LEGO-Symbol.png" alt="Logo Screenshot" width="180">
</p>

# 📊 LEGO Set Explorer (Power BI)

## 🧭 Project Overview

This project is an interactive Power BI dashboard that analyzes airline flight performance, as well as delays and cancellations across airports, airlines, and time periods.

The dashboard enables users to explore delay patterns, compare airline performance, identify airports with the highest delays and traffic, and monitor flight trends through a variety of visualizations and KPIs.

It was developed as part of the "Beginner Power BI: Airline Flight Delay Report" Maven Crash Course of Maven Analytics, during May-Jun/2026, in which I assume the role of a Data Analyst for the Federal Aviation Administration

---

## 📚 Learning Context

Despite the fact that the crash course offers a full walkthrough covering each step of the BI workflow, I wanted to add and expand on the dataset analysis. The report is enhanced with additional features, answers are provided for even more business questions, and the overall analysis experience is more visually appealing and thorough.

Through this project I practiced and improved skills such as:

* Building a structured data model   
* Writing DAX measures for business metrics  
* Creating field parameters for visualization flexibility  
* Creating dedicated tooltips for visuals  
* Designing interactive dashboards   
* Applying UI design principles to enhance the UX   

---

## 📁 Dataset Source

The dataset used in this project was provided in the crash course, which contains information about nearly 2,000,000 commercial flights from major US airports.

---

## 🎯 Business Approach

Taking a look at the data from a business point of view, through this project the hypothetical executive team could have answers for several key questions, such as:

* How many flights were delayed or cancelled, and why?
* Which airlines had the best and worst delayed- or cancellation- rates?
* Which airports were the busiest and which experience the most delays?
* What time periods (months or days of a week) are airports "vulnerable" to delays, or even cancellations?
* How does the location of an airport impact all of the above?

---

## 🧩 Data Model

The data model of this project uses the Star Schema approach. The dimension tables connect to the fact table with one-to-many (1-*) relationships.

Key components:

* Fact table: **Flights**
* Dimension tables (Lookup tables):

  * Airlines
  * Airports
  * Cancellation_codes

A new Calendar table was created, which enables efficient time intelligence calculations such as Month-over-Month analysis and trend reporting.

Over the course of the project some extra tables have been created, such as:
  * **Measure Table**: This table keeps all measures organized in folders.
  * **Calendar Table**: Enables efficient time intelligence calculations such as Month-over-Month analysis and trend reporting.
  * **Airports Measure Selection**, **Rate Measure Selection** and **Delay Reason Measure Selector**: These field parameters allow greater flexibility in specific visuals, enriching the UI/UX.

---

## 🧮 Key Measures (DAX)

The most important KPIs of this project should answer the most common (and critical) questions, and be displayed at the top of the Main Report. These are:

* Total Flights
* Total Delayed
* Total Cancelled
* On-Time Rate
* Delayed Rate
* Cancelled Rate

Those KPIs were calculated using DAX functions. Some of them are:

```DAX
Total Flights = COALESCE(COUNTROWS(flights), 0)

Total Delayed = COALESCE(CALCULATE([Total Flights], flights[STATUS]="Delayed"), 0)

Cancelled Rate = DIVIDE([Total Cancelled], [Total Flights], 0)
```

These measures allow dynamic aggregation across filters and visuals.

---

## 🖼️ Dashboard Preview

### Main Report

![Main Report Screenshot](images/Screenshot_1-Main_Report.png)

### Delay Report

![Delay Report Screenshot](images/Screenshot_2-Delay_Report.png)

### Delay Map

![Delay Map Screenshot](images/Screenshot_3-Delay_Map.png)

---

## ✨ Dashboard Features

This Power BI project includes:

* **Menu for easier navigation across the report**
* **Interactive slicers and filters**
* **Monthly airline- and airport- performance analysis**
* **Delay and cancellation reasons analysis**
* **Geographical analysis with immersive maps of airports**
* **Field parameter slicers for versatile charts**
* **Custom tooltips for key visuals**

---

## 🔍 Key Insights

Some insights identified from the analysis:

* About **2 million flights were delayed** in a year's span (35.9% of total flights) and just about **90k flights were cancelled** (1.5%).
* The biggest **delays** happen due to a **Late Aircraft**. On the other hand, most flights get **cancelled** because of the **Weather**.
* The airline with the highest rate of **delayed** flights is **Spirit Air Lines** (48.5%), while the airline with the lowest is **Delta Air Lines Inc.** (28.6%).
* The airline with the highest rate of **cancelled** flights is **American Eagle Airlines Inc.** (5.1%), which is almost  double the rate of the second-highest. The airline with the lowest is **Hawaiian Airlines Inc.** (0.2%).
* The biggest **arrival delays** (on average minutes) occur in **Wilmington Airport in Wilmington,DE** with a whopping 30.32 minutes (+6.3 minutes from the second).
* The busiest airport during the course of the year is **Aspen-Pitkin County Airport in Aspen,CO**, hosting over **4k flights** (about 4x times of the second's).
* **Flights are more probable to get delayed or cancelled during December-March and in June**.
* **Most flights get delayed on Thursdays and Fridays. Most flights get cancelled from Sundays to Tuesdays**.
* **Flights from remote airports and big cities experience higher delayed and cancellation rates**.
* **Some airports are operated only from specific airlines. As a result, those airlines struggle to keep their numbers undifferentiated.**.
* **Further geographic analysis helps identify regional operational bottlenecks**.
