# Python-Image-Processing-Script

import xarray as xr
import matplotlib.pyplot as plt
import numpy as np
import netCDF4 as nc
file_path = r"C:\your file_path .nc”
ds = xr.open_dataset(file_path)

# Extract data from the dataset
lat_data = ds['lat'].values
lon_data = ds['lon'].values
altitude_data = ds['altitude'].values
amplitude_high_gain_data = ds['amplitude_high_gain'].values
amplitude_low_gain_data = ds['amplitude_low_gain'].values
time_data = ds['time'].values

# Transpose the data
amplitude_low_gain_data = np.transpose(amplitude_low_gain_data)
amplitude_high_gain_data = np.transpose(amplitude_high_gain_data)

# Create subplots to display multiple radar stratigraphy variables
fig, axes = plt.subplots(nrows=1, ncols=2, figsize=(12, 6))

# Plot first variable
im1 = axes[0].imshow(amplitude_low_gain_data, cmap='gray', aspect='auto')
axes[0].set_title('Amplitude Low Gain')
fig.colorbar(im1, ax=axes[0])  # Associate colorbar with the first image

# Plot second variable
im2 = axes[1].imshow(amplitude_high_gain_data, cmap='gray', aspect='auto')
axes[1].set_title('Amplitude High Gain')
fig.colorbar(im2, ax=axes[1])  # Associate colorbar with the second image

# Display the plot
plt.tight_layout()  # Ensures proper spacing between subplots

# Extract and format the time, latitude, longitude, and altitude information
time_str = f"Time: {time_data}"
lat_str = f"Latitude: {lat_data}"
lon_str = f"Longitude: {lon_data}"
altitude_str = f"Altitude: {altitude_data}"

# Position the information outside the plot area using figtext
plt.figtext(0.70, 0.98, time_str, fontsize=8, va='center')       # Move time information down
plt.figtext(0.35, 0.95, lat_str, fontsize=8, va='center')    # Move latitude information down
plt.figtext(0.35, 0.99, lon_str, fontsize=8, va='center')    # Move longitude information down
plt.figtext(0.33, 0.02, altitude_str, fontsize=8, va='bottom')

# Display the plot
plt.show()
