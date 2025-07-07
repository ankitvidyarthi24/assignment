# Dynamic Pricing for Urban Parking Lots

Capstone Project | Summer Analytics 2025  
Organized by: Consulting & Analytics Club × Pathway

## Project Overview

Urban parking spaces are a limited yet highly demanded resource. Static pricing models often lead to inefficient usage — either through overcrowding or underutilization. This project aims to design and implement a dynamic pricing engine that adjusts parking prices in real time based on demand, traffic, vehicle type, queue length, and special days.

The pricing system is built using basic economic principles and implemented from scratch using only NumPy, Pandas, and Pathway (for real-time simulation). Bokeh is used for live visualization.

## Tech Stack

- Python
- Pandas and NumPy – data manipulation and numerical calculations
- Bokeh – interactive visualization
- Pathway – real-time data ingestion and simulation
- Google Colab – development environment
- GitHub – version control

## Architecture Diagram

```mermaid
graph TD
    A[Raw CSV Data] --> B[Preprocessing in Pandas]
    B --> C[Model 1: Linear Pricing]
    B --> D[Model 2: Demand-Based Pricing]
    D --> E[Normalize Demand & Adjust Price]
    E --> F[Bokeh Plot]
    D --> G[Pathway Stream Ingestion (Real-Time)]
    F --> H[User Visualization]
    G --> H
```

## Project Architecture & Workflow

### 1. Data Loading & Preprocessing
- Read the dataset from CSV containing 73 days of records across 14 parking lots.
- Combined date and time fields to create a timestamp column.
- Cleaned column names and standardized features.

### 2. Model 1: Baseline Pricing
- Simple linear model:
  ```python
  price_t+1 = price_t + alpha * (occupancy / capacity)
  ```
- Purpose: acts as a basic reference model.

### 3. Model 2: Demand-Based Pricing
- Constructed a custom demand function:
  ```
  demand = α(occupancy/capacity) + β(queue) − γ(traffic) + δ(special_day) + ε(vehicle_weight)
  ```
- Normalized demand score between 0 and 1
- Final price = BasePrice * (1 + λ * normalized_demand)
- Smoothed output by clipping prices between $5 and $20

### 4. Bokeh Visualization
- Created interactive time-series plots to compare Model 1 vs Model 2 pricing
- Used tooltips and hover features for detailed insights

### 5. Optional Extension: Model 3 (Planned)
- Competitive pricing based on lat-long and nearby lot prices
- Suggest rerouting or adjusting based on nearby lot conditions

### 6. Pathway Integration
- Simulates real-time data stream
- Future goal: real-time price updates and alerts based on live conditions

## Documentation

- notebook.ipynb – full implementation with all models, plots, and markdowns
- report.pdf – optional final report (if provided)
- pricing_engine.py – optional modularized pricing logic (planned)

## Conclusion

This project demonstrates how dynamic pricing can improve urban parking utilization by responding to real-world demand signals in real time. The logic is modular, extendable, and ready for competitive and live deployment with further development.

Feel free to fork and experiment!
