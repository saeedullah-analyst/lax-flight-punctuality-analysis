# LAX Flight Punctuality Analysis

Aviation analytics | Power BI | DAX | 1.26 million flight records | 2015–2017

---

This is the capstone Power BI project, analysing three years of flight data at Los Angeles International Airport. The goal was to establish a shared performance baseline across airport departments — identifying which carriers, directions, times of day, and seasons generate the most delay friction.

Cancelled and diverted flights are excluded from the analysis. A flight is defined as not punctual if it deviates 5 minutes or more from its scheduled slot in either direction.

**[View the Dashboard PDF](1_Flugpünktlichkeitsanalyse.pdf)**

---

## Technical Stack

| Layer | Tool / Method |
|---|---|
| BI Tool | Power BI Desktop |
| ETL | Power Query — heavy log ingestion, status filtering, time/date isolation |
| Data Model | Directional split: arrival and departure tracked as separate analytical dimensions |
| Visualisations | Time-series line charts, heat matrices, pie charts, Top-N ranking cards |

---

## Dataset

- 1,264,229 flight records across 2015, 2016, and 2017
- Each record includes: carrier, direction (arrival/departure), scheduled time, actual time, delay duration, flight status

---

## Overall Punctuality

| Status | Records | Share |
|---|---|---|
| Not punctual | 886,882 | 70.15% |
| Punctual | 377,347 | 29.85% |

Average delay across all affected flights: **26 minutes**

---

## Airport Volume by Carrier

Four carriers account for 67.6% of all LAX traffic in the dataset:

| Carrier | Flights | Share |
|---|---|---|
| Southwest Airlines | 245,910 | 19.45% |
| American Airlines | 229,420 | 18.15% |
| Delta Air Lines | 190,391 | 15.06% |
| SkyWest Airlines | 189,640 | 15.00% |

---

## Key Findings

### Arrivals are significantly more delayed than departures

| Direction | Not Punctual Rate |
|---|---|
| Departures | 58% |
| Arrivals | 82% |

Incoming flights carry nearly all the systemic delay load. This points to upstream causes — long-haul schedule drift, air traffic sequencing — rather than ground-side processing at LAX itself. The implication for operations is that arrival gates and ground crew need to absorb delays that originate elsewhere.

### Highest absolute delay volumes by carrier

- **Arrivals:** American Airlines recorded the highest total count of late inbound flights
- **Departures:** Southwest Airlines logged the most delayed outbound flights — 164,731 late departures, representing 18.57% of the entire delay database

These numbers reflect volume as much as performance. Both carriers are the two largest operators at LAX, so raw counts need to be read alongside their overall footprint.

### Highest average delay duration by carrier

| Carrier | Avg Delay | Total Delayed Flights |
|---|---|---|
| Envoy Air | 40 min | small footprint |
| Frontier Airlines | 31 min | small footprint |
| JetBlue Airways | 30 min | 22,874 (2.58% of database) |

Envoy Air and Frontier have the longest average delays but relatively few flights. JetBlue is the more operationally significant finding — similar average delay duration but a much larger presence at the airport, meaning the impact compounds across more flights.

### Delays follow predictable time patterns

**By season:** Delays peak in Q3 (summer travel) and again in late December. Both align with known passenger volume spikes.

**By weekday:** Fridays and early weekdays (Monday/Tuesday) show the highest delay concentration, driven by commercial travel demand.

**By hour:** Total delayed flight volume grows steadily through the day. However, average delay *duration* peaks in the early morning hours — not when total volume is highest. This suggests late-night backlog or early ground crew constraints are creating processing friction before the main rush begins, not during it.

---

## DAX Measures

```
// Total flights
Total Flights = COUNTROWS(fact_flights)

// Not punctual count
Not Punctual =
CALCULATE(
    COUNTROWS(fact_flights),
    fact_flights[punctuality_status] = "Not Punctual"
)

// Punctuality rate
Punctuality Rate % =
DIVIDE(
    CALCULATE(COUNTROWS(fact_flights), fact_flights[punctuality_status] = "Punctual"),
    COUNTROWS(fact_flights),
    0
)

// Average delay duration
Avg Delay (min) =
AVERAGEX(
    FILTER(fact_flights, fact_flights[delay_minutes] > 0),
    fact_flights[delay_minutes]
)
```

---

## Project Impact

| Finding | Operational Use |
|---|---|
| Arrivals at 82% not-punctual rate | Reallocate ground staff toward inbound gates |
| Early morning delay duration spike | Review overnight handover and early crew scheduling |
| JetBlue: 30-min avg delay at scale | Prioritise gate compliance review |
| Q3 and December seasonal peaks | Pre-position additional resources in advance |
| 1.26M records in one dashboard | Replaced fragmented department reports with unified baseline |

---
