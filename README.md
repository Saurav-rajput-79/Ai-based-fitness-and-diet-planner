# 🥗 Personalized Diet Recommendation System

## Project Overview

This project utilizes two primary datasets to build a foundation for a personalized diet recommendation system. The goal is to match user profiles and dietary needs with a comprehensive, nutritionally-balanced food database to generate tailored meal plans and nutritional targets.

The repository contains:
1.  A **Master Food Database** with detailed nutritional information and dietary compatibility flags.
2.  A **Diet Recommendation Engine Dataset** containing user profiles, calculated biometric data (BMI, BMR), and personalized macronutrient and caloric targets.

---

## 🎯 Project Goals

The core objectives of this project include:

1.  **Data-Driven Nutritional Targeting:** Establishing a robust dataset of personalized daily caloric and macronutrient requirements based on individual biometrics, health goals, and activity levels.
2.  **Comprehensive Food Cataloging:** Curating a clean and categorized food database with essential nutritional values and specific health flags (e.g., Diabetic Safe, BP Safe).
3.  **Recommendation Engine Development:** Laying the groundwork for an algorithm that can recommend specific meals from the food database that collectively meet the personalized daily nutritional targets.

---

## 📁 Data Files Overview

### 1. `master_food_dataset_v5_clean.csv` - The Food Database

This file serves as the main catalog of food items. It includes key nutritional information and boolean flags for quick filtering based on common dietary restrictions.

| Column Name | Description | Data Type | Example Values |
| :--- | :--- | :--- | :--- |
| `Food_items` | Name of the food item. | Object | 'Idli #1', 'Dosa #1' |
| `calories` | Total calories per serving. | Integer | 82, 168 |
| `protein_g` | Protein content in grams. | Float | 1.05, 3.06 |
| `fat_g` | Fat content in grams. | Float | 0.49, 7.96 |
| `carb_g` | Carbohydrate content in grams. | Float | 17.72, 26.28 |
| `sugar_g` | Sugar content in grams. | Float | 0.1, 1.85 |
| `sodium_mg` | Sodium content in milligrams. | Integer | 40, 213 |
| `meal_category` | The typical meal the item is consumed in. | Object | 'Breakfast', 'Snack', 'Dinner' |
| `is_veg_final` | Boolean: Is the item vegetarian? | Boolean | True, False |
| `diabetic_safe` | Boolean: Is the item safe for diabetic individuals? | Boolean | True, False |
| `bp_safe` | Boolean: Is the item safe for individuals with high blood pressure (low sodium)? | Boolean | True, False |

### 2. `final_engineered_dataset.csv` - The Profile & Target Dataset

This file contains profiles and the calculated, *personalized* nutritional targets for various users. It is the output of the dietary logic and engineering process.

| Column Name | Description | Data Type | Example Values |
| :--- | :--- | :--- | :--- |
| `Age`, `Gender`, `Height_cm`, `Weight_kg` | User biometrics. | Integer/Float/Object | 30, 'Male', 170.0, 70.0 |
| `Goal` | The user's weight goal. | Object | 'maintain', 'gain', 'lose' |
| `Diabetic`, `High_BP` | User's health conditions. | Object | 'Yes', 'No' |
| `Activity_Level` | User's physical activity intensity. | Object | 'Moderate', 'Sedentary' |
| `BMI`, `BMR`, `activity_factor` | Calculated physiological metrics. | Float | 24.22, 1617.5, 1.55 |
| `Daily_Calories` | Total recommended daily caloric intake. | Integer | 2504, 2312 |
| `target_protein_g`, `target_fat_g`, `target_carb_g` | Recommended daily macronutrient targets in grams. | Float | 70.0, 83.5, 368.1 |
| `cal_breakfast`, `cal_lunch`, `cal_dinner`, `cal_snacks` | Calorie split for each meal. | Integer | 551, 776, 876, 301 |
| `Diet_Recommendation` | Overall descriptive diet type. | Object | 'Balanced', 'Low-Carb' |

---

## 📈 Potential Analyses and Use Cases

The datasets can be utilized for a variety of tasks in data science, machine learning, and application development:

### Data Science / Analytics
* **Nutritional Pattern Analysis:** Analyze the distribution of macronutrients across different meal categories and food types.
* **Correlation Studies:** Investigate the relationship between user biometrics (`BMI`, `BMR`) and their calculated nutritional targets (`Daily_Calories`, `target_protein_g`).
* **Dietary Safety Insights:** Analyze which foods are most/least compatible with common health conditions (Diabetes, High BP).

### Machine Learning
* **Recommendation Model:** Develop a constraint satisfaction or optimization model to select a combination of `Food_items` that meets a user's `Daily_Calories` and macronutrient targets.
* **Classification:** Build a classifier to predict the optimal `Diet_Recommendation` based on a user's biometrics and goals.
* **Predictive Modeling:** Train a model to predict meal-specific calorie targets (`cal_breakfast`, etc.) from the primary user inputs.
