import streamlit as st
import numpy as np
import matplotlib.pyplot as plt

# Dummy function to predict solar energy based on sunlight and temperature
def predict_solar_energy(temperature, sunlight_hours):
    return 0.5 * sunlight_hours * temperature


# Dummy function to predict water demand based on temperature and population
def predict_water_demand(temperature, population):
    return 0.3 * population * temperature


# Streamlit app interface
st.title("Smart Water and Energy Management System")

# Collect user inputs
temperature = st.slider(
    "Enter the temperature (°C)",
    min_value=0,
    max_value=40,
    step=1
)

sunlight_hours = st.slider(
    "Enter the sunlight hours per day",
    min_value=0,
    max_value=12,
    step=1
)

population = st.slider(
    "Enter the population size",
    min_value=100,
    max_value=10000,
    step=100
)

# Predict button
if st.button("Predict"):
    # Calculate solar energy and water demand
    solar_energy = predict_solar_energy(temperature, sunlight_hours)
    water_demand = predict_water_demand(temperature, population)

    # Display results
    st.write(f"Estimated Solar Energy Production: {solar_energy:.2f} kWh")
    st.write(f"Estimated Water Demand: {water_demand:.2f} liters/day")

    # Visualize results using Matplotlib
    fig, ax = plt.subplots(1, 2, figsize=(10, 5))

    # Plot Solar Energy Production
    ax[0].bar(["Solar Energy"], [solar_energy], color="orange")
    ax[0].set_title("Solar Energy Production (kWh)")
    ax[0].set_ylabel("Energy (kWh)")

    # Plot Water Demand
    ax[1].bar(["Water Demand"], [water_demand], color="blue")
    ax[1].set_title("Water Demand (liters/day)")
    ax[1].set_ylabel("Water (liters)")

    st.pyplot(fig)
