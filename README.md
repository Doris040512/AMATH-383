# AMATH 383 Final Project  
### Investigating Drivers of Influenza Seasonality in Washington State (2010–2019)

This project explores a central question in mathematical epidemiology:  
**What drives the strong winter pattern of influenza in temperate regions?**  
Is it **cold weather**, or is it simply a **built-in annual cycle**?

Using ten years of weekly influenza-like illness (ILI) data from CDC ILINet and daily temperature records from NOAA, I compare three models:

1. **Temperature-Driven Linear Model**  
2. **Seasonal Cosine (Pure Annual Cycle) Model**  
3. **Mechanistic SIR Model with Temperature-Dependent β(t)**  

The goal is to determine which mechanism better explains the shape, timing, and magnitude of influenza activity in Washington State.

---

## 📁 Project Contents

| File | Description |
|------|-------------|
| `AMATH 383 Final Project (4).ipynb` | Complete analysis notebook (data cleaning, EDA, regression models, SIR model, plots). |
| `Avg_Temp.csv` | NOAA weekly averaged temperature data (2010–2019). |
| `ILI_Cases.csv` | Weekly influenza-like illness counts from CDC ILINet. |
| `FINAL_MERGED_DATA.csv` | Cleaned and merged dataset used for all models. |
| `timeseries_plot.png` | Time-series plot of temperature vs. ILI. |
| `scatter_plot.png` | Scatter plot of temperature vs. ILI cases. |
| `model_comparison_temp_vs_seasonal.png` | Comparison of linear and SIR model predictions vs real data. |

---

## 🔍 Project Overview

Seasonal influenza peaks every winter, but there are two competing explanations:

### **(1) Environmental Mechanism**  
Cold weather improves viral survival and increases indoor crowding → higher transmission.

### **(2) Calendar-Based Mechanism**  
Flu follows a yearly cycle driven by behavior, holidays, and school schedules → independent of weather.

To test these hypotheses, the notebook fits three models:

---

## 📊 Summary of Models and Results

### **Model 1 — Temperature-Driven Linear Regression**
\[
\widehat{\text{ILI}}(t) = \beta_0 + \alpha_T \,(T_\mathrm{ref} - T(t))
\]

- Captures the rise in cases during colder weeks  
- **Train RMSE: 30.1**  
- **Test RMSE: 63.0**  
- Best AIC among the simple models

---

### **Model 2 — Pure Seasonal Cosine Model**
\[
\widehat{\text{ILI}}(t) = \beta_0 + \delta \cos(2\pi t / 52)
\]

- Matches the broad yearly cycle but  
- Fails to capture sharp winter peaks  
- **Train RMSE: 36.3**  
- **Test RMSE: 68.8**

---

### **Model 3 — Mechanistic SIR Model (Temperature-Driven β)**
\[
\beta(t) = \beta_0 + \alpha (50 - T(t))
\]

- Uses the full SIR differential equation system  
- Produces a smooth epidemic curve  
- Underestimates large peaks  
- **Train RMSE: 52.6**  
- **Test RMSE: 88.8**

---

## 🏁 Final Takeaways

- The **temperature-driven model** fits the flu data noticeably better than a pure calendar-based cycle.  
- Temperature helps explain *both* the timing and the size of seasonal outbreaks.  
- The SIR model connects well to course material but is too rigid to match real-world weekly data.  
- Additional factors (strain differences, school schedules, humidity) likely play a role in unusually large seasons like 2017–18.

---

## 📦 Requirements

This project was run in  
**Python 3.10** with the following packages:

