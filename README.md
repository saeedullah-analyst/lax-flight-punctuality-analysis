# Power BI Capstone Case Study: Los Angeles International Airport (LAX) Flight Punctuality Matrix

## Profile and Core Competencies / Kompetenzprofil

### English Summary
* Project Goal: Processed 1.26 million historical flight records to evaluate operational punctuality profiles, rank carrier delay severities, and isolate time-series congestion bottlenecks at Los Angeles International Airport (LAX).
* Technical Skills Applied: End-to-End ETL Data Cleansing, Directional Matrix Segmentation (Arrival vs. Departure), Top-N Carrier Ranking, Anomaly Filtering, and Temporal Trend Modeling.
* Business Value: Consolidated massive aviation operational streams into a unified executive reporting system, revealing that arrival vectors account for the highest systemic delay stress and identifying critical morning processing gaps.

### Deutsche Zusammenfassung
* Projektziel: Analyse von 1,26 Millionen Flugdatensätzen zur Bewertung von Pünktlichkeitsprofilen, Ranking von Fluggesellschaften nach Verzögerungsintensität und Isolierung zeitlicher Engpässe am Flughafen Los Angeles (LAX).
* Angewandte Hard Skills: End-to-End ETL-Datenbereinigung, direktionale Matrixsegmentierung (Ankunft vs. Abflug), Top-N-Airlines-Ranking, Anomaliefilterung und zeitliche Trendmodellierung.
* Geschäftlicher Nutzen: Konsolidierung massiver Flugbetriebsdaten in ein einheitliches Reporting-System, das zeigt, dass Ankunftsvektoren das höchste Verzögerungsrisiko tragen, und kritische Engpässe am frühen Morgen identifiziert.

---

## Project Assets and Management Report

To review the detailed data visualizations, temporal trend charts, and interactive page layouts constructed for this aviation intelligence operation, access the document below:

* 👉 **[Download the Full PDF Dashboard and Management Report Presentation](Dashboard-Report-Presentation.pdf)**

---

## 1. Project Overview and Operational Scenario
Managing airline punctuality at major international transit hubs is a primary requirement for scheduling optimization and airport asset allocation. Operating as a Data Analyst for the airport management board of fLAirport, this capstone project conducts a routine operational audit of Los Angeles International Airport (LAX). The goal is to establish a shared baseline of performance insights across multiple internal airport departments and identify specific scheduling clusters where internal processes should be adjusted.

The analytical infrastructure evaluates historical flight records spanning a three-year cycle from **2015 to 2017**. To guarantee a clean operational focus, flights that were completely canceled or diverted are intentionally filtered out of this baseline. 

A flight is explicitly defined as **Unpünktlich (Not Punctual)** if it exhibits an arrival or departure time-delta deviation of **5 minutes or greater** (either early or late) relative to its scheduled slot.

## 2. Technical Stack and Competency Matrix
* Business Intelligence Tool: Power BI Desktop
* Data Engineering & Cleansing: Power Query ETL pipeline (Ingestion of heavy transaction logs, structural filtration of status attributes, and dynamic time/date isolation).
* Relational Modeling: Implemented direct database connections, separating transactional tracking data across active Directional Dimensions (Arrival vs. Departure).
* Visualizations and Analytical Scaffolding: Time-series Line Charts (by Month, Week, Day, and Hour), High-Density Heat Matrices, Segmented Pie Charts, and Top-N Row-Ordered Ranking Cards.

---

## 3. Key Metrics Discovered
* Total Operational Dataset Ingested: 1,264,229 Gross Flight Records
* Overall Punctuality Distribution (LAX Base Scale):
  * Unpünktliche Flüge (Not Punctual): 886,882 records (70.15%)
  * Pünktliche Flüge (Punctual): 377,347 records (29.85%)
* Macro System Turnaround Benchmark: 26 Minutes average delay duration per flight.
* Market Share Concentration (Top 4 Carriers driving 67.6% of overall airport volume):
  1. Southwest Airlines Co.: 245,910 total flights (19.45%)
  2. American Airlines Inc.: 229,420 total flights (18.15%)
  3. Delta Air Lines Inc.: 190,391 total flights (15.06%)
  4. SkyWest Airlines Inc.: 189,640 total flights (15.00%)

---

## 4. Root Cause Diagnostics and Analytics Insights

### Directional Matrix Asymmetry (Arrivals vs. Departures)
Evaluating punctuality across directional flight flows uncovered an operational asymmetry between arrival and departure patterns:
* Departure Vector Punctuality: Registries show a 58% unpünktlich level for outgoing flights.
* Arrival Vector Bottlenecks: Systemic friction spikes significantly for incoming traffic, recording an extreme **82% unpünktlich level**. Incoming flights carry the vast majority of processing delays, showing that upstream scheduling or long-distance flight management generates the highest logistical pressure on LAX ground control.

### Absolute Delay Densities vs. Top-Tier Carriers
Cross-referencing absolute volume metrics against individual carrier accounts isolated the specific brands generating the largest overall friction within the facility:
* Inbound Congestion: American Airlines Inc. registered the highest absolute count of late arrivals.
* Outbound Congestion: Southwest Airlines Co. held the highest absolute count of delayed departures, logging 164,731 unpünktliche flights (representing 18.57% of the total delay database).

### Top 3 Carriers by Average Delay Duration
To identify severe performance anomalies independent of a carrier's market size, the model isolated the Top 3 airlines with the highest average delay durations:
* Benchmark Leader: **Envoy Air** logged the highest average delay, peaking at **40 minutes** per affected flight, followed by **Frontier Airlines Inc.** (31 minutes), and **JetBlue Airways** (30 minutes).
* Market Share Context: While Envoy Air and Frontier Airlines Inc. generate high average durations, they represent a small fraction of overall airport volume. JetBlue Airways stands out as a higher risk due to its larger operational footprint, accounting for 22,874 delayed movements (2.58% of the total database).

### Chronological Volatility and Trend Matrices
Time-series charts mapping flight counts and duration indicators across Years, Quarters, Months, and Hours revealed recurring seasonal and daily patterns:
* Macro Seasonal Spikes: Delays peak during the mid-year travel season (Quarter 3) and spike again during late December winter holidays.
* Weekly Performance Deficits: Frustration points concentrate heavily on Fridays and early weekday slots (Mondays/Tuesdays) due to peak commercial passenger travel.
* Daily Operational Swings: The absolute volume of unpünktliche flights increases steadily throughout the day after the early morning rush. However, **average delay times peak during the early morning hours**, showing that late-night backlogs or early ground crew constraints create severe processing friction for early arrivals.

---

## 5. Documented Business Value and Project Impact
* Consolidated 1.26 million transactional flight lines into a single, high-impact overview report, giving multiple airport departments a unified performance baseline.
* Isolated the operational variance between arrival and departure punctuality, enabling ground logistics to reallocate staff to high-friction incoming flights.
* Flagged Envoy Air, Frontier, and JetBlue as the top 3 lines for high average delay durations, giving airport management clear parameters to review specific carrier gate compliance.
* Mapped chronological delay peaks across months, weekdays, and hours, allowing terminal operations teams to adjust staff schedules during high-risk morning and weekend slots.

---

