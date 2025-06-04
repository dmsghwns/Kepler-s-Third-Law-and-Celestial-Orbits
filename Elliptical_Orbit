import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# Solar system planet data (a: AU, e: eccentricity)
data = {
    "Planet": ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"],
    "a": [0.387, 0.723, 1.000, 1.524, 5.204, 9.582, 19.189, 30.071],  # Semi-major axis (AU)
    "e": [0.205, 0.007, 0.017, 0.093, 0.048, 0.054, 0.047, 0.009]     # Eccentricity
}

df = pd.DataFrame(data)

# Simulate elliptical orbits
theta = np.linspace(0, 2 * np.pi, 1000)  # True anomaly (0 to 2π)
plt.figure(figsize=(10, 10))
plt.axis('equal')
plt.xlim(-35, 35)
plt.ylim(-35, 35)
plt.xlabel('X (AU)')
plt.ylabel('Y (AU)')
plt.title('Elliptical Orbits of Planets')

# Sun's position (at focus)
plt.scatter([0], [0], color="orange", s=100, label="Sun")

# Plot elliptical orbit for each planet
colors = ['blue', 'orange', 'green', 'red', 'purple', 'brown', 'pink', 'gray']
for i, row in df.iterrows():
    a = row["a"]
    e = row["e"]
    planet = row["Planet"]
    # Elliptical orbit equation: r(theta)
    r = a * (1 - e**2) / (1 + e * np.cos(theta))
    # Convert to Cartesian coordinates
    x = r * np.cos(theta)
    y = r * np.sin(theta)
    # Plot orbit
    plt.plot(x, y, color=colors[i], label=planet)

# Add legend and grid
plt.legend()
plt.grid()
plt.show()
