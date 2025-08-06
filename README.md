# Olist Brazil E-Commerce: A Deep Dive into Fulfillment Time Prediction & Geospatial Analysis

## 1. Project Overview

This project is an end-to-end data science practice targeting Brazil's largest e-commerce platform, Olist, with the core business objective of **enhancing the customer's logistics experience**.

Given Brazil's vast territory and complex logistics landscape, accurately predicting order **Fulfillment Time** is crucial for the platform to optimize operational efficiency, improve customer satisfaction, and set precise Estimated Delivery Dates.

In this project, we went beyond building a simple "black-box" prediction model. Our core challenges and highlights include:

*   **In-depth Feature Engineering**: From 9 raw, separate data tables, we constructed a "Data Titan" with over 40 fields through sophisticated data merging and fusion. Building on this, we creatively engineered a rich set of derivative features from three dimensions: **time**, **commerce**, and most critically, **space**.
*   **Geospatial Analysis**: For the first time, we successfully applied the `Haversine` formula to calculate the real-world **physical straight-line distance** between customers and sellers, integrating the powerful variable of "geography" into our model.
*   **Hybrid Intelligence Modeling**: We explored the fusion of "human intelligence" and "AI intelligence." We not only built a baseline `LightGBM` model based on manually crafted features but also, for the first time, successfully utilized an `Autoencoder` neural network to extract high-dimensional abstract features. We proved that this "AI-empowered" hybrid model could significantly **reduce the prediction error (RMSE) by 14.80%**!
*   **Industry-Standard Experiment Management**: We used `MLFlow` throughout the project to professionally track and manage all our **experiment parameters**, **performance metrics**, and **model artifacts** in a reproducible manner.
*   **Actionable Business Insights Visualization**: We ultimately created a "data movie" with a five-act story in `Tableau`. It not only showcases the model's accuracy but also uncovers a series of profound, actionable business insights from the geographical distribution of errors and product category characteristics, regarding **systematic overestimation**, **opportunities for creating 'wow' customer experiences**, and **future directions for model optimization**.

This project fully demonstrates a complete, end-to-end capability in data-driven problem-solving, from raw data exploration and complex feature creation to advanced model application and, finally, the extraction of valuable business insights.

## 2. Key Findings & Visualizations

Our core insights unfold through the following five-act data story:

### Act I: The Curse of Distance
As expected in a country as vast as Brazil, physical distance is the most fundamental factor affecting logistics efficiency. The scatter plot below clearly illustrates the undeniable, strong positive correlation between fulfillment time and the distance between customer and seller.
*Image Placeholder: `01_distance_curse.png`*

### Act II: The Landscape of Reality
To understand the geographical distribution of fulfillment times, we first mapped the average actual fulfillment time for each Brazilian state. The darker the color, the longer the waiting time. We can clearly see that the remote northwestern states present the most severe logistical challenges.
*Image Placeholder: `02_reality.png`*

### Act III: The Gaze of AI
Next, we mapped the average fulfillment time as predicted by our model. Comparing this with the "reality map," we were stunned to find that our LightGBM model almost perfectly replicates the real world's macro-logistical patterns. This proves our model's powerful predictive capabilities and its deep understanding of the business.
*Image Placeholder: `03_prediction.png`*

### Act IV: The Scream of the Error
However, beneath this perfect replication lies a deeper truth. This "error heatmap" reveals a core tendency of our model: a systematic "pessimism" (overestimating fulfillment time). All states show a negative error (represented in red), with the lightest shades indicating the regions where the model overestimates the most. This is no longer just an "error"; it's a **strategic opportunity** for us to create 'wow' customer experiences and crush the competition in these areas!
*Image Placeholder: `04_error_heatmap.png`*

### Act V: The Fate of the Category
Finally, we shift our focus from "space" to the "product" itself. This bar chart clearly reveals the inherent "prediction difficulty" associated with different product categories. The longer the bar, the larger the average absolute error for that category. We found that bulky items like "home appliances" and "furniture" are the most difficult to predict. This provides a clear strategic direction for future model optimization, focusing on category-specific models.
*Image Placeholder: `05_category_destiny.png`*

## 3. How to Reproduce

1.  **Clone the Repository**: `git clone https://github.com/sunhuan258-cyber/Olist-Fulfillment-Forecast.git` (Note: Please use the new repository name you've chosen).
2.  **Set Up Environment**: Ensure your Python environment has the core libraries installed: `pandas`, `numpy`, `lightgbm`, `mlflow`, `scikit-learn`, `haversine`, `jupyterlab`.
3.  **Prepare Data**: Place the 9 original Olist `.csv` datasets into the `data/` folder.
4.  **Run Merging Notebook**: Open and run `notebooks/OLIST-Link.ipynb` to generate `olist_final_analysis_dataset.csv`.
5.  **Run Main Notebook**: Open and run `notebooks/OLIST.ipynb` to perform feature engineering, model training, MLFlow tracking, and to generate the final `olist_visualization_data_FULL.csv`.
6.  **Explore Visualization**: Open the `巴西业务.twbx` file (requires Tableau Desktop or Tableau Public) to interactively explore our data story.