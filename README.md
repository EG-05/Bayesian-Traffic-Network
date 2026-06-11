# Bayesian-Traffic-Network

A probabilistic graphical model for urban traffic congestion in Karachi, Pakistan. Built using GeNIe Modeler (SMILE/XDSL format).

- [GeNIe Modeler](https://www.bayesfusion.com/) (free academic license available)

## How to Run

1. Open GeNIe Modeler
2. **File → Open** → select `karachi_traffic_bn.xdsl`
3. The full DAG loads with all 13 nodes, arcs, and CPTs pre-defined
4. To run inference: **Monitor → Set Evidence** on any node, posteriors update instantly

## Network Overview

**13 variables** across 3 layers:

- **Root (6):** TimeOfDay, DayOfWeek, WeatherCondition, RoadWork, SignalFailure, PublicTransport
- **Intermediate (4):** TrafficVolume, PrivateVehicleDensity, RoadCondition, AccidentOccurrence
- **Target:** CongestionLevel
- **Leaf (2):** CommuteDelay, EconomicImpact

## General Probabilities 

**| Node | States | Probabilities |
| TimeOfDay | Peak / OffPeak / | Night 0.35 / 0.45 / 0.20 |
| DayOfWeek | Weekday / Weekend / Holiday | 0.57 / 0.29 / 0.14 |
| WeatherCondition | Clear / Rainy / Monsoon | 0.65 / 0.20 / 0.15 |
| RoadWork | Present / Absent | 0.25 / 0.75 |
| SignalFailure | Yes / No | 0.30 / 0.70 |
| PublicTransport | Adequate / Inadequate | 0.20 / 0.80 |**


## Use Cases

| # | Evidence Set | Key Result |
|---|---|---|
| UC1 | Peak + Weekday + Monsoon | P(Severe Congestion) = **0.87** |
| UC2 | Night + Weekend + Signal Failure | P(Accident) spikes to **0.28** despite low volume |
| UC3 | Accident observed + Peak + Weekday | P(Severe) = **0.91**, P(High Economic Impact) = **0.82** |

