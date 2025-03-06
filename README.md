# Airbnb Booking Rate Prediction Project

## Overview

This project focuses on predicting the booking rate of Airbnb properties.  The goal is to provide actionable insights for Airbnb hosts to optimize their listings, enhance the booking experience for guests, and enable data-driven decision-making for stakeholders.

## Business Problem

Airbnb hosts face the challenge of maximizing the occupancy rate of their properties.  This project addresses this by developing a machine learning model to predict the probability of a listing having a high booking rate.

## Objectives

*   Develop a machine learning model to accurately predict the probability of an Airbnb listing having a high booking rate.
*   Leverage historical data, including property attributes and host information, to provide actionable insights.

## Target Audience

*   **Airbnb Hosts:** Optimize listings (pricing, amenities) to increase booking rates.
*   **Potential Guests:** Identify listings with a high likelihood of availability and positive experiences.
*   **Investors and Analysts:** Evaluate investment opportunities and market trends.

## Key Features

The model utilizes a variety of features, including:

*   **Property Attributes:** `property_type`, `room_type`, `accommodates`, `bathrooms`, `bedrooms`, `price`, `cleaning_fee`
*   **Host Information:** `host_response_time`, `host_response_rate`, `host_acceptance_rate`
*   **Booking Details:** `guests_included`, `extra_people`, `minimum_nights`, `availability_30`, `availability_60`, `cancellation_policy`
*   **Amenities:** Count of amenities offered.
*   **Flags:** `is_superhost`, `is_verified`, `is_instant_bookable`
*   **Text-Mined Features:**  Keywords extracted from listing descriptions related to access and transit (e.g., "wifi", "laundri", "airport", "subway").

### Feature Engineering Highlights:

*   `property_type`: Grouped into "Residential", "Lodging", "Unique Accommodation", "Outdoor Accommodation", and "Other".
*   `cancellation_policy`: Combined less common strict policies into a single "strict" category.
*   `features`:  Created boolean flags for "is\_superhost", "is\_verified", and "is\_instant\_bookable".
*   Missing values were imputed using mean or majority values based on relevant categories.
*   Text mining was used to create features from the listing descriptions.

## Models Used

The following models were explored:

*   **Logistic Regression:**  Initial baseline model.
*   **Boosting Model (GBM):**  Experimented with boosting, but performance was not satisfactory.
*   **Random Forest:**  Final winning model.

### Random Forest Details

*   **Library:** `randomForest`
*   **Training AUC:** 0.9999581 (likely overfit)
*   **Hyperparameter Tuning:**
    *   `mtry`: Values tried: 3, 5, 9, 11. Final value: 9
    *   `ntree`: Values tried: 500, 1000, 1200, 1500. Final value: 500

## Results

The Random Forest model achieved a high training AUC, but showed signs of overfitting. The estimated generalization performance was around 0.9.

## Learning Curves

The training AUC curve from the Random Forest model indicated a perfect fit to the training data, reinforcing concerns about overfitting.  This led to good performance on the training set but poorer performance on the test data (AUC = 0.8737).

## Code

*   The R code for training the final Random Forest model and generating predictions can be found in the R script, lines 346-361.

## Challenges and Takeaways

*   **Challenges:**
    *   Ensuring team cohesion and communication.
    *   Maintaining consistent data formatting.
    *   Identifying the most important features.
    *   Model selection and evaluation strategy.
*   **What We Would Do Differently:**
    *   Adopt a more structured approach to model selection from the beginning.
    *   Prioritize controlling overfitting early in the process.
    *   Focus on careful feature selection and preparation upfront.

## Future Work

*   Mitigate overfitting issues with advanced regularization techniques.
*   Incorporate a broader range of text-based features (e.g., neighborhood overview, house rules).
*   Systematically optimize hyperparameters and evaluate performance using regularization.

## Advice for Future Teams

*   Start early and focus on identifying the right set of features.
*   Perform thorough feature engineering.
*   Experiment with a variety of models and hyperparameter settings.
