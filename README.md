# STATS 507 Final Project – Machine Learning for Recycled Polypropylene Tensile Strength

This repository contains the code for my MATH 507 course final project.  
The goal is to use small-scale machine learning models to predict the tensile strength of mechanically recycled polypropylene (PP) based on recycling history, composition (e.g., glass fiber content), and processing method, and to extract interpretable structure–property relationships from a compiled literature dataset.

The project compares three approaches:

1. **Linear regression** – baseline model  
2. **Random forest regression** – non-linear, interpretable tree ensemble  
3. **HuggingFace transformer (DistilBERT)** – simple text–based regression baseline

---

## Repository Structure

- `Step_1to4_Data_cleaning_matrix_building_Regression&randomforest.py`  
  End-to-end script that:
  - Loads the raw dataset from Excel  
  - Cleans and filters the data  
  - Builds a model-ready feature matrix (numeric + one-hot encoded categorical features)  
  - Splits the data into train/test sets  
  - Trains **linear regression** and **random forest** models  
  - Reports MAE / RMSE / R² for both models  
  - Computes random-forest feature importance  

- `Step_5_Apply_huggingfaceHF_model.py`  
  Script that:
  - Loads the curated dataset (same source as above)  
  - Prepares a simple text-based representation or tabular input for a HuggingFace model  
  - Fine-tunes a **DistilBERT** model for regression using the `transformers` Trainer API  
  - Evaluates the model (MAE, RMSE, R²) on the test set  



## Data

The models are trained on a curated dataset compiled from published literature that reports tensile strength of PP under:

- multiple mechanical recycling cycles,  
- different polymer grades (homo-PP, block-PP, GFPP),  
- different compositions (glass fiber, talc, contaminants), and  
- different processing methods (injection molding, melt extrusion, compounding + molding).

Each record includes at least:

- recycle_cycles
- polymer grade
- processing method  
- weight fractions of PP, glass fiber, talc, and various contaminants  
- measured/reported tensile_strength_MPa

Two datasets used for the project can also be found in this repo:
    507_final_project_data-2.xlsx        # original curated dataset
    model_ready_matrix.xlsx              # cleaned / encoded matrix used in models
