
#  Dynamic Pricing for Urban Parking Lots

**Capstone Project – Summer Analytics 2025**  
By: *Palak Singhal*

---

##  Project Overview

This project aims to optimize urban parking space usage through **real-time dynamic pricing**. By integrating traffic, demand, occupancy, and competitor analysis, the pricing engine adapts fluidly to ensure efficient lot usage, reduce congestion, and maximize revenue.

Key Features:
- Real-time pricing updates (every 30 mins)
- Demand-based and competition-aware logic
- Smooth price variation (bounded 0.5x–2x)
- Supports different vehicle types and special days
- Optional rerouting logic for over-capacity lots

---

##  Tech Stack

| Component      | Technology      |
|----------------|------------------|
| Language       | Python (3.10+)   |
| Data Analysis  | pandas, numpy    |
| Real-Time Engine | Pathway        |
| Visualizations | Bokeh            |
| Notebook       | Google Colab     |
| Documentation  | Markdown, Mermaid |

---

##  Architecture Diagram

```mermaid
flowchart TD
    A[Raw Dataset (CSV)] --> B[Streaming Simulator (Pathway)]
    B --> C[Feature Extraction]
    C --> D[Pricing Models]
    D --> E1[Baseline Model]
    D --> E2[Demand-Based Model]
    D --> E3[Competitive Model]
    E1 --> F[Price Output]
    E2 --> F
    E3 --> F
    F --> G[Live Dashboard (Bokeh)]
    F --> H[Suggested Rerouting]
```

---

##  Project Workflow

1. **Data Ingestion:**  
   A historical dataset of 14 parking lots over 73 days is streamed with Pathway to mimic real-time.

2. **Feature Engineering:**  
   At each time step, occupancy, queue length, traffic, special day, vehicle type, and location info are extracted.

3. **Model 1 – Baseline Linear:**  
   Increases price linearly with occupancy. Serves as a benchmark.

4. **Model 2 – Demand-Based:**  
   Calculates a composite demand score from key variables. Applies tanh smoothing to keep variation bounded.

5. **Model 3 – Competitive:**  
   Adjusts prices using nearby competitor pricing (distance-weighted). Suggests rerouting logic if a lot is overloaded.

6. **Visualization:**  
   Real-time price changes are plotted using Bokeh and displayed in a browser or notebook interface.

7. **Deployment Ready:**  
   Designed for seamless integration into a production-grade Pathway deployment.

## Future Improvements

- Learn optimal weights via reinforcement learning or bandit algorithms
- Include weather and event data from public APIs
- Train a classifier to predict overflow and trigger rerouting
- Deploy full system using Docker + Pathway cloud

