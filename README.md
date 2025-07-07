# **Parky: Dynamic Parking Pricing Dashboard 🚗💰📈**

Welcome to **Parky**, a real-time dynamic pricing engine designed to revolutionize urban parking management\! This project leverages streaming data, economic principles, and machine learning to optimize parking space utilization, reduce congestion, and maximize revenue.

## **🌟 Overview**

Urban parking spaces are a finite and highly sought-after resource. Static pricing often leads to inefficiencies – either overcrowded lots during peak hours or underutilized spaces during off-peak times. **Parky** addresses this challenge by simulating a dynamic pricing system that adapts to real-time demand, competitive landscapes, and environmental conditions.

This project demonstrates a robust framework for:

* **Real-time Data Ingestion:** Processing live streams of parking data.  
* **Intelligent Pricing:** Applying economic theory and custom-built ML models to predict optimal prices.  
* **Dynamic Adjustments:** Continuously updating prices based on evolving conditions.  
* **Interactive Visualization:** Providing real-time insights into pricing behavior and utilization trends.

## **💡 Problem Statement**

The goal is to create an intelligent, data-driven pricing engine for 14 urban parking spaces. This engine must process real-time data streams, apply basic economic theory, and utilize machine learning models (built from scratch using NumPy and Pandas) to continuously emit pricing predictions. The ultimate aim is to improve parking space utilization, reduce overcrowding, and enhance revenue.

## **✨ Key Features**

* **Real-time Data Pipeline:** Powered by [Pathway](https://pathway.com/), ensuring continuous processing of incoming parking data.  
* **Custom Pricing Models:** Implementations of baseline, demand-based, and competitive pricing strategies using only NumPy and Pandas.  
* **Dynamic Price Adjustments:** Prices adapt instantly to changes in occupancy, queue length, traffic conditions, and special events.  
* **Interactive Visualizations:** Live dashboards built with [Bokeh](https://bokeh.pydata.org/) to monitor price evolution, utilization, and demand patterns.  
* **Comprehensive Data Utilization:** Leverages rich features including location, capacity, occupancy, queue length, vehicle type, traffic conditions, and special day indicators.

## **🏗️ Project Architecture & Workflow**

The system is designed as a real-time data processing pipeline:

    graph TD  
        A\[Raw Parking Data Stream\] \--\> B(Pathway Data Ingestion);  
        B \--\> C{Feature Engineering};  
        C \--\> D\[Dynamic Pricing Logic\];  
        D \-- Predicted Prices \--\> E\[Real-time Price Output\];  
        C \-- Occupancy, Queue, Traffic \--\> F\[Utilization & Demand Analysis\];  
        E \--\> G(Bokeh Visualizations);  
        F \--\> G;  
        G \--\> H\[Interactive Dashboard\];

        subgraph Pricing Engine  
            C  
            D  
            E  
            F  
        end

        style A fill:\#f9f,stroke:\#333,stroke-width:2px  
        style B fill:\#bbf,stroke:\#333,stroke-width:2px  
        style C fill:\#ccf,stroke:\#333,stroke-width:2px  
        style D fill:\#ddf,stroke:\#333,stroke-width:2px  
        style E fill:\#eef,stroke:\#333,stroke-width:2px  
        style F fill:\#ffc,stroke:\#333,stroke-width:2px  
        style G fill:\#cfc,stroke:\#333,stroke-width:2px  
        style H fill:\#fcc,stroke:\#333,stroke-width:2px

1. **Data Ingestion:** Raw parking data, including occupancy, queue length, and environmental factors, is ingested as a continuous stream.  
2. **Feature Engineering:** Pathway processes this raw data, extracting and transforming features relevant for pricing decisions.  
3. **Dynamic Pricing Logic:** Custom-built models (using NumPy and Pandas) apply economic principles and machine learning to predict optimal prices based on the processed features.  
4. **Real-time Price Output:** The calculated prices are continuously emitted for each parking lot.  
5. **Analysis & Visualization:** Key metrics like utilization, occupancy, and queue lengths are analyzed. All outputs are fed into Bokeh to create interactive, real-time dashboards that visually justify pricing behavior and show performance trends.

## **🚀 Getting Started**

To run this project locally, follow these steps:

### **Prerequisites**

* Python 3.9+  
* Google Colab (recommended execution environment)

### **Installation**

Clone the repository and install the necessary libraries:

    git clone https://github.com/your-username/Parky.git \# Replace with your actual repo link  
    cd Parky  
    pip install pathway bokeh numpy pandas \--quiet

### **Running the Project**

The core logic and execution are within the Jupyter Notebook.

1. **Open the Notebook:** Open ParkSense.ipynb (or Parky (1).ipynb if that's the primary notebook) in Google Colab.  
2. **Run Cells:** Execute the cells sequentially. The final cell containing pw.run() will start the real-time data pipeline and update the Bokeh plots continuously.

       \# Example snippet from the notebook  
        import pathway as pw  
       from bokeh.plotting import figure, show  
       from bokeh.io import output\_notebook

       \# ... (Your data loading, pricing logic, and Bokeh plot setup) ...

       \# This triggers the real-time data stream processing and updates the Bokeh plots continuously.  
       \# %%capture \--no-display suppresses output in the notebook interface, but the Bokeh plots will still update live.  
       print("Starting Pathway pipeline. Plots will update below...")  
       pw.run()

## **📊 Dataset**

The project utilizes dataset.csv, containing data from 14 urban parking spaces over 73 days, sampled at 18 time points per day (8:00 AM to 4:30 PM).

Key features include:

* Latitude, Longitude: Location information for proximity calculations.  
* Capacity, Occupancy, QueueLength: Parking lot status.  
* VehicleType: Type of incoming vehicle.  
* TrafficConditionNearby, IsSpecialDay: Environmental and event indicators.  
* LastUpdatedDate, LastUpdatedTime: Temporal information.

## **📈 Results & Visualizations**

The dynamic pricing system is designed to provide real-time insights into pricing, utilization, and efficiency.

### **Real-time Pricing Outputs**

Bokeh plots display the "Up-to-the-Minute Pricing" for each parking lot, showcasing the responsiveness of different pricing models:

* **Model 1 (Baseline):** Represents a static or less dynamic approach, with prices remaining constant for extended periods.  
* **Model 2 (Demand-Based):** Shows continuous price fluctuations directly responding to real-time demand indicators like occupancy and queue length.  
* **Model 3 (Competitive):** Exhibits pricing behavior influenced by external factors, potentially mimicking competitor prices or reacting to traffic conditions.

These models are often compared side-by-side to evaluate their performance:

### **Utilization and Occupancy Trends**

The system enables analysis of:

* **Occupancy Patterns:** Time-series plots revealing daily/weekly cycles and peak usage.  
* **Utilization Rate:** Calculated as (Occupancy / Capacity) \* 100%, showing efficiency over time.  
* **Queue Length Dynamics:** Identifying periods of unmet demand and overcrowding.  
* **Impact of External Factors:** How TrafficConditionNearby and IsSpecialDay influence demand.

### **Revenue and Efficiency Improvements (Expected)**

Once the dynamic pricing logic is fully implemented, the system is expected to demonstrate:

* **Increased Revenue:** By optimizing prices, the system aims to capture higher revenue during peak demand and encourage usage during off-peak hours.  
* **Reduced Overcrowding:** Higher prices during peak times should mitigate queue lengths and improve flow.  
* **Enhanced Utilization:** Lower prices during off-peak hours should attract more users, increasing overall space utilization.

## **🚀 Future Work**

This project provides a robust foundation. Future enhancements could include:

* **Advanced ML Models:** Implementing time series forecasting (ARIMA, LSTM) and deep learning for more accurate demand prediction.  
* **Reinforcement Learning:** Framing pricing as an RL problem to enable adaptive learning of optimal strategies.  
* **User Feedback Integration:** Incorporating qualitative feedback and behavioral economics principles for improved user acceptance.  
* **External Data Integration:** Adding real-time event data, weather data, and public transport information for more precise demand forecasting.  
* **Scalability & Deployment:** Exploring distributed computing, containerization (Docker), orchestration (Kubernetes), and cloud deployment for production readiness.

## **📁 Repository Contents**

    .  
    ├── ParkSense.ipynb           \# Main Jupyter Notebook with Pathway pipeline and Bokeh setup  
    ├── Project\_Report.pdf        \# Detailed project report  
    ├── README.md                 \# This README file  
    ├── dataset.csv               \# The raw dataset used for simulation  
    ├── parking\_data\_stream.csv   \# (Optional) Simulated real-time data stream  

## **🤝 Contributing**

Contributions are welcome\! Please feel free to open issues or submit pull requests.

Developed with ❤️ for Summer Analytics 2025 Capstone Project
