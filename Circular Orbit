import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# Solar system planet data (T: years, a: AU, e: eccentricity)
data = {
    "Planet": ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"],
    "T": [0.241, 0.615, 1.000, 1.881, 11.862, 29.457, 84.011, 164.791],  # Orbital period (years)
    "a": [0.387, 0.723, 1.000, 1.524, 5.204, 9.582, 19.189, 30.071],      # Semi-major axis (AU)
    "e": [0.205, 0.007, 0.017, 0.093, 0.048, 0.054, 0.047, 0.009]         # Eccentricity
}

df = pd.DataFrame(data)

# Calculate T^2 and a^3
df["T^2"] = df["T"] ** 2
df["a^3"] = df["a"] ** 3
df["T^2/a^3"] = df["T^2"] / df["a^3"]

# Calculate perihelion and aphelion distances
df["r_min"] = df["a"] * (1 - df["e"])  # Perihelion
df["r_max"] = df["a"] * (1 + df["e"])  # Aphelion

# Print results
print(df[["Planet", "T", "a", "e", "T^2/a^3", "r_min", "r_max"]])

# Plot: T^2 vs a^3, with point size scaled by eccentricity
plt.scatter(df["a^3"], df["T^2"], s=200 * df["e"], color="blue", label="Planets")
plt.plot(df["a^3"], df["a^3"] * df["T^2/a^3"].mean(), color="red", label="Fit")
plt.xlabel("a^3 (AU^3)")
plt.ylabel("T^2 (years^2)")
plt.title("Kepler's Third Law: T^2 vs a^3 with Eccentricity")
plt.legend()

# Add planet name labels
for i, row in df.iterrows():
    plt.text(row["a^3"], row["T^2"], row["Planet"], fontsize=8)

plt.grid()
plt.savefig("kepler_third_law_with_eccentricity.png")
plt.show()
