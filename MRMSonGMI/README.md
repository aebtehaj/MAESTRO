# MRMS Precipitation Data Mapped on GMI Orbits

## 1. Overview

This repository contains Multi-Radar Multi-Sensor (MRMS) 2-minute precipitation data that has been spatially and temporally mapped onto Global Precipitation Measurement (GPM) Microwave Imager (GMI) orbits crossing the Continental United States (CONUS). The dataset is organized into two folders:

- **Flag Folder**: Contains precipitation type classification data (Rain = 1, Snow = 2, clear = 0, no coverage = -3, outside of CONUS = NAN)
- **Rate Folder**: Contains precipitation rate data in mm/hr

## 2. The Method

The mapping process followed these steps:

1. Created a 3-dimensional Python list to handle the spatial-temporal matching of corresponding GMI files crossing CONUS with corresponding MRMS filenames.

2. Developed an algorithm for approximately finding MRMS points falling inside of GMI grids:
   - For each MRMS point, we identified the nearest GMI point
   - Then assigned all MRMS points to the GMI point that was nearest to them
   
   ![Example of gathering MRMS points for a GMI grid](Example/method_2.png)
   
3. To prevent gathering MRMS points outside of the GMI orbit:
   - Created fake padding at the edges of the GMI orbit
   - Processed the spatial mapping with this padding in place
   - Removed the padding after implementation of the spatial mapping was complete
   
   ![Adding padding to GMI orbit edges](Example/method_1.png)

## 3. A Sample

Below are sample visualizations of the data:

| Original MRMS Data | Mapped on GMI Orbit |
|:------------------:|:-------------------:|
| ![Original MRMS Data](Example/MRMS.png) | ![Mapped Data](Example/Mapped.png) |
| 2022/12/23 at 04:04:00 | GMI Orbit 50100 (04:02:00 - 04:10:00, 2022/12/23) |


