## 💎 Capstone-project
   This report presents a capstone project titled "Dynamic Pricing for Urban  Parking Lots using Pathway and Bokeh". The primary goal was to build a  smart pricing engine that adjusts parking prices based on demand, traffic, and  other real-world conditions using Python, Pathway, and Bokeh

   # Dataset Overview
      The dataset consisted of 18,368 rows with the following features:
           Occupancy
           Capacity
           QueueLength
           TrafficConditionNearby
           IsSpecialDay
           VehicleType
       These features were used to compute both static and dynamic parking prices.

  # Model 1: Linear Pricing   
    This model calculates the parking price using the formula:
        Model1_Price = BasePrice + alpha * (Occupancy / Capacity)
        Where:
           BasePrice = $10
           alpha = 5
    It reflects simple pricing based only on occupancy, without considering 
    contextual or demand-based features.

  # Model 2: Demand-Based Pricing
    This model uses the following inputs:
       Occupancy / Capacity
       Queue Length
       Traffic Conditions (low=1, average=2, high=3)
       Vehicle Type (car=1.0, bike=0.5, truck=1.5)
       Is Special Day
     
      Demand is calculated as:
         Raw Demand = alpha*(Occ/Cap) + (beta*Queue) –( gamma*Traffic) 
         + (delta*Special) + (epsilon*VehicleWeight)
          Then: 
         Model2_Price = BasePrice * (1 + lambda * NormalizedDemand)
  # Pathway Integration
      We used the Pathway streaming engine to simulate real-time pricing:
         Data was ingested using pw.io.csv.read() in static mode.
         Prices were calculated using @pw.udf for Model 1 and Model 2.
         Results were written to final_output.csv.
      This showed how a data pipeline could be built for real-time applications.
  # Bokeh Visualization
     Visualized pricing using Bokeh:
        1. Model 1 vs Model 2 pricing against occupancy
        2. Time-series price simulation for a parking lot
        3. Interactive visual dashboards (Colab-compatible)
     These helped justify why Model 2 pricing was more responsive and fair.
  # Conclusion
     This capstone demonstrates how dynamic pricing systems can be 
    implemented using real-time data pipelines with Pathway and visualized 
    using Bokeh. Model 2 clearly showed better adaptiveness. The entire solution 
    is deployable and scalable for urban use cases.
