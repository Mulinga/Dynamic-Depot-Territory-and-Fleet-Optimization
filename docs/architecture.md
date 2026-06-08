# Architecture

## Data Flow

Depot -> Route -> Shop -> Order

## Inputs
- Orders
- Shops
- Zones
- Routes
- Vehicles
- Depots
- Dispatch History

## Layer 1: Data Validation
- Missing values
- Territory integrity
- Polygon validation

## Layer 2: Territory Analytics
- Coverage analysis
- Overlap detection
- Unzoned shops
- Territory density

## Layer 3: Demand Analytics
- Depot demand
- Route demand
- Daily demand
- Drop demand

## Layer 4: Optimization Engine

Inputs:
- Weight demand
- Shop count
- Truck capacity
- Territory constraints

Outputs:
- Recommended trucks
- Recommended depot splits
- Depot pressure score
- Utilization score

## Fleet Strategy

Truck Types:
- 2500kg
- 4500kg

Target:
- 50–70 drops/truck
- >85% utilization

## Future Enhancements
- OR-Tools routing
- Demand forecasting
- Dynamic territory generation
- Cost optimization
