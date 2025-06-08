# Python Image Processing Script for Geophysical Data

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

## 🗒️ Python Script

This python script will be utilized to display radargrams with visualization. Modifying the file path of the .nc file, importing relevant libraries, and extracting data values is what the script entails.


```python
  
import xarray as xr

import matplotlib.pyplot as plt

import numpy as np

import netCDF4 as nc

file_path = r"C:\your file_path .nc”

ds = xr.open_dataset(file_path)

lat_data = ds['lat'].values

lon_data = ds['lon'].values

altitude_data = ds['altitude'].values

amplitude_high_gain_data = ds['amplitude_high_gain'].values

amplitude_low_gain_data = ds['amplitude_low_gain'].values

time_data = ds['time'].values

amplitude_low_gain_data = np.transpose(amplitude_low_gain_data)

amplitude_high_gain_data = np.transpose(amplitude_high_gain_data)

fig, axes = plt.subplots(nrows=1, ncols=2, figsize=(12, 6))

im1 = axes[0].imshow(amplitude_low_gain_data, cmap='gray', aspect='auto')

axes[0].set_title('Amplitude Low Gain')

fig.colorbar(im1, ax=axes[0])

im2 = axes[1].imshow(amplitude_high_gain_data, cmap='gray', aspect='auto')

axes[1].set_title('Amplitude High Gain')

fig.colorbar(im2, ax=axes[1])

plt.tight_layout() 

time_str = f"Time: {time_data}"

lat_str = f"Latitude: {lat_data}"

lon_str = f"Longitude: {lon_data}"

altitude_str = f"Altitude: {altitude_data}"

plt.figtext(0.70, 0.98, time_str, fontsize=8, va='center')

plt.figtext(0.35, 0.95, lat_str, fontsize=8, va='center')

plt.figtext(0.35, 0.99, lon_str, fontsize=8, va='center')

plt.figtext(0.33, 0.02, altitude_str, fontsize=8, va='bottom')

plt.show()

```


__________________________________________________________________________________________________________________________

## Note:

I will only provide two radargrams with no sensitive information (scientific data values and geographic area) as this project was completed through a summer research training opportunity.

---

## 📊 Results

### Radargrams Generated through Image Processing Script

#### Radargram 1 

![radargram 1](https://github.com/user-attachments/assets/b830cf67-c581-43ba-b671-9d05c57c58d4)


#### Radargram 2

![r3](https://github.com/user-attachments/assets/f624ed3a-248f-43a8-8a93-334fefb9f9f4)

---
## References

1) National Aeronautics and Space Administration (NASA) MUREP INCLUDES Proactive Pathways of Excellence to Engage Minority Students in Aerospace Engineering (PEMS)
2) The University of Texas Institute of Geophysics 











