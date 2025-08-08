# Tesla Battery Health-Aware Routing – Problem Brief

## 1. Problem Statement
Tesla’s current Trip Planner is designed to minimize travel time by automatically selecting optimal Supercharger stops. While this is effective for speed, it does not account for long-term battery health degradation, which is influenced by high charging rates, high ambient temperatures, elevation changes, and aggressive driving patterns.  

The goal of this project is to develop a simulation-driven routing system that recommends routes for Tesla Model Y drivers in New Delhi that minimize State of Health (SoH) loss, while keeping travel time competitive.

## 2. Tesla Integration Points
- **Inputs**: 
  - Start location (latitude, longitude)
  - End location (latitude, longitude)
  - Current State of Charge (SoC, %)
  - Ambient temperature (°C)
  - Elevation profile along route
  - Road speed limits
- **Outputs**: 
  - Recommended route (.rou.xml)
  - Suggested charging stops (if applicable)
  - Estimated trip time
  - Estimated SoH impact
- **Data Sources**: 
  - OpenStreetMap (OSM) for road networks
  - SUMO for traffic simulation
  - Tesla Model Y efficiency data from public sources
  - NASA Battery Dataset for degradation modeling
  - Weather data APIs (for temperature impact)

## 3. Metrics of Success
- **Primary**: Percentage reduction in predicted SoH loss compared to the shortest-time baseline route.
- **Secondary**: Percentage increase in travel time compared to the baseline.
- **Target Goal**: Achieve ≥15% reduction in SoH loss with ≤5% additional travel time.

## 4. Project Inputs & Outputs
### Inputs:
- Tesla Model Y specifications:
  - Battery capacity: 75 kWh
  - Weight: ~2003 kg
  - Drag coefficient: 0.23
  - Efficiency curve: Speed vs Wh/km table
- Road network of New Delhi from OSM, converted to SUMO format (.net.xml)
- Elevation data integrated into road network
- Ambient temperature profile for the simulation period
### Outputs:
- Route file for SUMO (.rou.xml)
- Trip energy consumption log (CSV)
- Predicted battery SoH change per trip

## 5. Deliverables (Stage 1)
- `docs/problem_brief.pdf` — finalized problem scope
- SUMO simulation baseline (shortest-time route)
- Custom Model Y vehicle profile for SUMO
- Battery degradation model implementation
- Route optimizer with SoH scoring
- Comparative results: baseline vs optimized routing
