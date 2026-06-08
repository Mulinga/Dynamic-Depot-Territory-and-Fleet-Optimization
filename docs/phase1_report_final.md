# Twiga Dynamic Depot & Fleet Optimization Initiative
## Phase 1 Progress Report
### Data Discovery, Territory Assessment and Optimization Readiness

**Author:** Charles Mulinga  
**Department:** Data Science & Logistics Analytics  
**Date:** June 2026

# Executive Summary

This project was initiated to investigate how Twiga can improve logistics efficiency through data-driven depot balancing and fleet optimization.

Currently, vehicle allocation decisions are largely operational and reactive, relying on depot experience, historical routing patterns, and daily demand fluctuations. As the network continues to grow through the onboarding of new shops, changing delivery territories, and evolving customer demand, the complexity of fleet allocation and depot workload management increases significantly.

The long-term vision of this initiative is to build an intelligent optimization engine capable of recommending:

- Optimal truck allocation
- Dynamic depot balancing
- Territory adjustments
- Capacity planning decisions
- Cost reduction opportunities
- Future route optimization strategies

The ultimate outcome will be a decision-support system that enables Operations and Logistics teams to make faster and more informed planning decisions while maximizing truck utilization and minimizing transport costs.

# Business Problem

Twiga currently serves thousands of retail outlets across multiple operational depots.

As order demand fluctuates across regions, several challenges emerge:

## Uneven Depot Workloads

Some depots consistently process significantly more demand than others, leading to:

- Higher fleet pressure
- Reduced operational flexibility
- Increased transportation costs

## Fleet Underutilization

Vehicles may leave depots:

- Underloaded
- Serving fewer shops than optimal
- Covering inefficient delivery territories

## Territory Evolution

Operational territories are not static.

New shops are continually onboarded, creating:

- Territory expansion
- Territory overlap
- Unbalanced delivery workloads

# Project Objectives

- Determine optimal truck allocation by depot
- Identify overloaded and underutilized depots
- Optimize 2.5T and 4.5T fleet deployment
- Achieve 50–70 drops per truck
- Improve capacity utilization to 85–100%
- Build the foundation for dynamic depot creation

# Optimization Strategy

## Weight Utilization

| Vehicle Type | Capacity |
|-------------|----------:|
| Small Truck | 2,500 kg |
| Medium Truck | 4,500 kg |

Target Utilization: **85–100%**

## Drop Density Optimization

Target:

**50–70 drops per truck**

Weight utilization alone is insufficient. The optimization framework balances:

- Weight
- Number of drops
- Geographic coverage
- Depot workload

# Phase 1 Activities Completed

## Production Data Acquisition

| Dataset | Records |
|----------|---------:|
| Orders | 12,124 |
| Shops | 7,481 |
| Zones | 101 |
| Routes | 309 |
| Vehicles | 944 |
| Depots | 41 |
| Dispatch History | 123,357 |

## Operational Data Mapping

A complete operational hierarchy was established:

Depot → Route → Shop → Order

This creates traceability from customer demand back to operational depots.

## Territory Modelling

Territory boundaries were converted into geospatial polygons enabling:

- Coverage analysis
- Territory overlap analysis
- Future geospatial optimization

## Territory Validation

Results:

- Total Zones: 101
- Valid Geometries: 101
- Invalid Geometries: 0

Finding:

All territory geometries are valid and suitable for geospatial analytics.

## Territory Coverage Analysis

Coverage Rate: **97.71%**

Finding:

The current territory design provides excellent geographic coverage and supports future optimization efforts.

## Territory Overlap Analysis

Overlap Rate: **89.11%**

Finding:

The overlap appears operational rather than a geometry-quality issue. Further investigation is required before territory-driven optimization is implemented.

## Depot Demand Analysis

Top Demand Depots:

| Depot | Weight (kg) |
|---------|---------:|
| Embakasi | 92,785 |
| Syokimau | 81,780 |
| West Nairobi | 70,057 |
| Nairobi Central | 63,731 |
| Kiambu | 61,845 |

Key Insight:

Demand is unevenly distributed across the network. Embakasi currently processes approximately three times the demand processed by lower-volume depots, making it a strong candidate for future balancing strategies.

# Business Value Delivered

This initiative has already:

- Established a unified logistics data model
- Quantified depot workloads
- Validated territory coverage
- Identified territory overlap risks
- Created the foundation for fleet utilization analysis
- Identified high-pressure depots
- Prepared operational data for optimization modelling

# Current Project Status

| Component | Status |
|------------|---------|
| Orders | Complete |
| Shops | Complete |
| Routes | Complete |
| Depots | Complete |
| Vehicles | Complete |
| Dispatch History | Complete |
| Territory Boundaries | Complete |
| Territory Rationalization | In Progress |

## Optimization Readiness

Current readiness estimate: **85–90%**

The project has successfully completed discovery and validation and is ready to transition into optimization modelling.

# Phase 2: Dynamic Depot & Fleet Optimization

Planned outputs:

## Fleet Recommendations

- Number of 2.5T trucks required
- Number of 4.5T trucks required
- Truck utilization scores

## Depot Recommendations

- Depot pressure scores
- Dynamic depot split recommendations
- Demand balancing opportunities

## Cost Optimization

- Cost per kg delivered
- Cost per drop delivered
- Estimated transport savings

## Management Dashboards

- Depot demand ranking
- Fleet utilization distribution
- Drop-density analysis
- Territory coverage maps
- Depot pressure heatmaps

# Conclusion

Phase 1 successfully established the data foundation required to build a dynamic logistics optimization platform for Twiga.

Production logistics data has been validated, territory coverage has been assessed, depot demand patterns have been quantified, and key operational challenges have been identified.

The project is now ready to move into optimization modelling, where fleet allocation, depot balancing, vehicle utilization, and transportation cost reduction opportunities will be evaluated using production operational data.
