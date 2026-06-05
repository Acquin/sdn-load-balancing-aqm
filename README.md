# SDN Load Balancing with Katz Centrality and AQM

> Dynamic routing in Software-Defined Networks using Katz centrality 
> as a traffic-aware metric, integrated with Active Queue Management 
> for congestion control.

## Problem
Traditional static routing in data center networks doesn't adapt to 
real-time traffic conditions. This project implements a control-theoretic 
approach to dynamic load balancing in SDN.

## Key Ideas
- **Routing metric**: Katz centrality computed iteratively over the 
  network graph, updated per traffic epoch
- **Convergence guarantee**: Routing matrix updates converge under both 
  amplifying (κ > 1) and reducing (κ < 1) traffic conditions via 
  Banach fixed-point theorem
- **AQM integration**: Active Queue Management (CoDel/PIE) at each 
  switch to prevent buffer bloat

## Architecture
[Include a diagram image here — even a hand-drawn one photographed]

## Results
| Metric | Baseline (ECMP) | This work |
|---|---|---|
| Avg link utilization | 61% | 84% |
| 99th pctl latency | 18ms | 11ms |
| Packet loss rate | 2.3% | 0.6% |

(Replace with your actual results)

## Setup & Run
\```bash
git clone https://github.com/yourname/sdn-load-balancing-aqm
cd sdn-load-balancing-aqm
pip install -r requirements.txt
sudo python topology/fat_tree.py
python experiments/run_experiment.py
\```


## Research Context
This work is part of my MTech thesis at IIT Mandi. 
[Link to paper/preprint if available]
