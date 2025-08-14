#  Geospatial Image Processing and Visualization

## 🎯 Objective

* To process and visualize geophysical data stored in a .nc file using Python. The file follows the NetCDF4 data model and format, and the goal is to extract and render the data as a geographical image through certain python libraries.
---

First, you need to download the latest python version on the official website of Python. Use the pip command to get the modules you want via command line. 

---

##  📂 Python Modules 

<pre>pip install numpy

pip install matplotlib

pip install xarray

pip install netCDF4 </pre>

---

## 🐍 Python

Python will be utilized to display radargrams with visualization. Modifying the file path of the .nc file, importing relevant libraries, and extracting data values is what the process entails.


```python
  
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

```

__________________________________________________________________________________________________________________________

## 📊 Results

### Radargrams Generated through Image Processing Script

#### Radargram 1 

<img width="1541" height="713" alt="Radargram01" src="https://github.com/user-attachments/assets/3844dffe-0e95-42cf-8859-58bcdaa505fe" />


#### Radargram 2

<img width="1995" height="904" alt="Radargram02" src="https://github.com/user-attachments/assets/feda991c-8f72-47ad-8909-1c5690b100f4" />


#### Radargram 3

<img width="1717" height="1015" alt="Radargram03" src="https://github.com/user-attachments/assets/9009a91e-89f9-494a-a19a-9ed5bbc6c7e4" />

#### Radargram 4 

<img width="1728" height="1040" alt="Radargram04" src="https://github.com/user-attachments/assets/0f76ef2b-c7a0-4e7e-8f27-ce985c3ff7fb" />

#### Radargram 5

<img width="1684" height="1021" alt="Radargram05" src="https://github.com/user-attachments/assets/2e0af207-d57a-4cec-8c4f-257bcd703e9e" />

#### Radargram 6

<img width="1767" height="970" alt="Radargram06" src="https://github.com/user-attachments/assets/b9698ac2-fa5f-47e9-a996-a03c2df647e6" />


---
## References

1) National Aeronautics and Space Administration (NASA) MUREP INCLUDES Proactive Pathways of Excellence to Engage Minority Students in Aerospace Engineering (PEMS)
2) The University of Texas Institute of Geophysics 











