# Dynamic Depot Territory & Fleet Optimization

## Overview

Dynamic Depot Territory & Fleet Optimization is a geospatial analytics and operations research project designed to optimize logistics operations within large-scale FMCG distribution networks.

The project addresses three major challenges commonly encountered in distribution operations:

* Uneven depot workloads
* Low truck utilization
* Inefficient territory allocation

Rather than focusing solely on route optimization, this project introduces a multi-layer optimization framework that simultaneously improves:

1. Territory Design
2. Depot Allocation
3. Fleet Allocation

The result is a system capable of dynamically balancing delivery territories, creating operational depots when demand spikes, and allocating the most appropriate fleet while minimizing transportation costs.

---

## Business Problem

Distribution networks often operate using fixed territories and manually assigned fleet resources.

As the customer base grows, several operational challenges emerge:

* Some depots become overloaded while others remain underutilized.
* Delivery territories become imbalanced.
* New shops are added outside existing territories.
* Territories overlap due to changing operational requirements.
* Truck utilization decreases.
* Transportation costs increase.

Traditional routing systems optimize routes after territories have already been assigned.

This project optimizes the network before routing occurs.

---

## Objectives

The primary objective is to develop an intelligent logistics optimization engine capable of:

* Assigning shops to territories
* Detecting unzoned shops
* Detecting overlapping territories
* Balancing depot workloads
* Dynamically creating operational depots
* Optimizing truck allocation
* Maximizing fleet utilization
* Reducing transportation costs

---

## Project Architecture

```text
Orders
   │
   ▼
Territory Assignment
   │
   ▼
Depot Demand Aggregation
   │
   ▼
Dynamic Depot Creation
   │
   ▼
Truck Allocation
   │
   ▼
Route Optimization
   │
   ▼
KPI Dashboard
```

---

## Depot Network

The simulation is based on ten operational depots:

| Depot           |
| --------------- |
| Machakos        |
| Nairobi Central |
| Waiyaki Way     |
| Rongai          |
| Thika           |
| Kahawa          |
| Kiambu          |
| Syokimau        |
| Embakasi        |
| Eastlands       |

Certain depots are configured as dynamic depots.

Dynamic depots can be automatically split into operational territories whenever demand exceeds predefined thresholds.

### Dynamic Depots

* Machakos
* Nairobi Central
* Waiyaki Way
* Syokimau
* Embakasi
* Eastlands

### Static Depots

* Rongai
* Thika
* Kahawa
* Kiambu

---

## Territory Structure

The network consists of:

* 10 Depot Territories
* 30 Delivery Zones
* Approximately 10,000 Shops
* 90,000 Simulated Orders

Each delivery zone belongs to a depot territory.

```text
Embakasi
├── Pipeline
├── Tassia
└── Fedha

Eastlands
├── Umoja
├── Donholm
└── Kayole
```

---

## Geospatial Modeling

The system uses geographic polygons to model operational territories.

### Depot Polygons

Each depot is represented by a polygon boundary.

These boundaries are used for:

* Territory assignment
* Demand aggregation
* Depot balancing
* Capacity planning

### Zone Polygons

Each depot contains multiple delivery zones represented by sub-polygons.

Zones are used for:

* Workload balancing
* Territory optimization
* Delivery density calculations

### Point-In-Polygon Assignment

Every shop is assigned to a territory using geospatial analysis.

```text
Shop Coordinates
      │
      ▼
Zone Polygon
      │
      ▼
Depot Polygon
      │
      ▼
Assigned Territory
```

---

## Data Model

### Depots

```csv
depot_id
depot_name
latitude
longitude
dynamic_allowed
```

### Zones

```csv
zone_id
zone_name
depot_id
```

### Shops

```csv
shop_id
latitude
longitude
zone_id
depot_id
```

### Orders

```csv
order_id
shop_id
order_date
weight_kg
```

### Fleet

```csv
truck_id
capacity_kg
```

---

## Data Quality Monitoring

The project intentionally includes common operational challenges.

### Unzoned Shops

Unzoned shops are locations that fall outside all defined delivery territories.

Example:

```text
Shop A
Latitude: -1.250
Longitude: 36.950

Result:
Outside all territory polygons
```

These shops are flagged for review and reassignment.

---

### Overlapping Territories

Territory overlaps occur when a location belongs to more than one zone.

Example:

```text
Shop B
Inside Zone A
Inside Zone B
```

The system detects overlaps automatically and identifies affected shops.

---

## Dynamic Depot Creation

One of the most important features of the project is dynamic depot creation.

When demand exceeds a predefined threshold, additional operational territories are created.

Example:

### Before

```text
Embakasi
42,000 kg
```

### After

```text
Embakasi-1
21,000 kg

Embakasi-2
21,000 kg
```

These are virtual operational depots rather than physical facilities.

The objective is to:

* Balance workloads
* Reduce route complexity
* Improve truck utilization

---

## Fleet Optimization

The system supports multiple truck categories.

### Fleet Types

| Truck Type | Capacity  |
| ---------- | --------- |
| 3 Ton      | 3,000 kg  |
| 5 Ton      | 5,000 kg  |
| 7 Ton      | 7,000 kg  |
| 10 Ton     | 10,000 kg |

---

### Allocation Logic

The optimizer evaluates:

* Depot demand
* Territory demand
* Available truck capacity

The objective is to maximize utilization while minimizing the number of trucks deployed.

Example:

```text
Demand = 22,000 kg

Recommended Fleet

2 × 10 Ton Trucks
1 × 3 Ton Truck

Utilization = 95%
```

---

## Optimization Workflow

### Step 1

Assign shops to territory polygons.

### Step 2

Aggregate daily order demand.

### Step 3

Calculate territory workloads.

### Step 4

Create operational depots where required.

### Step 5

Allocate trucks based on demand.

### Step 6

Generate operational KPIs.

### Step 7

Optimize delivery routes.

---

## Key Performance Indicators

### Territory KPIs

* Shop Count
* Territory Area
* Weight Density
* Zone Utilization

### Depot KPIs

* Daily Demand
* Operational Depot Count
* Depot Utilization

### Fleet KPIs

* Truck Utilization
* Empty Capacity
* Trucks Required
* Cost per Kilogram Delivered

### Data Quality KPIs

* Unzoned Shops
* Overlapping Shops
* Territory Coverage

---

## Repository Structure

```text
twiga-depot-optimization/

├── data/
│   ├── depots.geojson
│   ├── depots.csv
│   ├── zones.csv
│   ├── shops.csv
│   ├── orders.csv
│   ├── fleet.csv
│   ├── overlaps.csv
│   └── unzoned_shops.csv
│
├── notebooks/
│   ├── 01_data_validation.ipynb
│   ├── 02_territory_analysis.ipynb
│   ├── 03_dynamic_depot_creation.ipynb
│   ├── 04_fleet_optimization.ipynb
│   └── 05_dashboard.ipynb
│
├── src/
│   ├── territory.py
│   ├── depots.py
│   ├── fleet.py
│   ├── routing.py
│   └── config.py
│
├── outputs/
│   ├── maps/
│   ├── reports/
│   └── dashboards/
│
├── requirements.txt
│
└── README.md
```

---

## Technology Stack

### Data Engineering

* Python
* Pandas
* NumPy

### Geospatial Analytics

* GeoPandas
* Shapely
* Folium

### Optimization

* Google OR-Tools
* Scipy

### Visualization

* Matplotlib
* Plotly
* Folium

---

## Future Enhancements

### Demand Forecasting

Predict future demand using:

* XGBoost
* LightGBM
* Random Forest

---

### Dynamic Territory Redesign

Automatically rebalance territories based on:

* Order volume
* Shop density
* Delivery distance

---

### Route Optimization

Use vehicle routing algorithms to:

* Minimize travel distance
* Minimize transport cost
* Improve delivery efficiency

---

### Real-Time Fleet Planning

Integrate live operational data for:

* Daily planning
* Capacity forecasting
* Fleet scheduling

---

## Expected Business Impact

The solution is designed to deliver measurable operational improvements.

Expected benefits include:

* Improved truck utilization
* Reduced transportation costs
* Better depot workload balancing
* Reduced manual planning effort
* Improved territory visibility
* Faster decision making
* Enhanced service coverage

By combining geospatial analytics, operations research, and logistics optimization, this project provides a foundation for intelligent distribution planning across large-scale FMCG networks.
