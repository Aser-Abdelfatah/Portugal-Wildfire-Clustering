# Portugal-Wildfire-Clustering
This is the open-source repo for my wildfire research done at University of Lausanne during summer 2023 as a part of Beucler Lab and in collaboration with Dr. Marj Tonini

## Work reproducibility:
The data is located in [Portugal_Dataset_Extraction/Datasets](https://github.com/Aser-Abdelfatah/Portugal-Wildfire-Research/tree/main/Portugal_Dataset_Extraction/Datasets) in tabular form and stored in CSV format. There are six datasets, three for undersampled unburned areas in Portugal and three for all burned areas in Portugal from April 2006 to September 2022. For either burned or non-burned data, one dataset includes meteorological data, one dataset include both meteorological and climatic data, and a third dataset includes meteorological and climatic data in addition to imputated data for missing values. The climatic data is computed as the average of the meteorological data over the entire time frame of the source datacube.
</br> The source datacube is the Mesogeos dataset, and the source code for it is located in [Mesogeos GitHub repository.](https://github.com/Orion-AI-Lab/mesogeos/tree/main) </br> 
  
 <details>  <summary>Datacube Variables <sup>1</sup></summary>

The original datacube contains the following variables:

- satellite data from MODIS (Land Surface Temperature (https://lpdaac.usgs.gov/products/mod11a1v061/), Normalized Vegetation Index (https://lpdaac.usgs.gov/products/mod13a2v061/), Leaf Area Index (https://lpdaac.usgs.gov/products/mod15a2hv061/))
- weather variables from ERA5-Land (max daily temperature, max daily dewpoint temperature, min daily relative humidity, 
max daily wind speed, max daily surface pressure, mean daily surface solar radiation downwards) (https://cds.climate.copernicus.eu/cdsapp#!/dataset/10.24381/cds.e2161bac?tab=overview)
- soil moisture index from JRC European Drought Observatory (https://edo.jrc.ec.europa.eu/edov2/home.static.html)
- population count (https://hub.worldpop.org/geodata/listing?id=64) & distance to roads (https://hub.worldpop.org/geodata/listing?id=33) from worldpop.org 
- land cover from Copernicus Climate Change Service (https://cds.climate.copernicus.eu/cdsapp#!/dataset/satellite-land-cover?tab=overview)
- elevation, aspect, slope and curvature from Copernicus EU-DEM (https://land.copernicus.eu/imagery-in-situ/eu-dem/eu-dem-v1.1?tab=download)
- burned areas and ignition points from EFFIS (https://effis.jrc.ec.europa.eu/applications/data-and-services)

Vriables in the cube:
| Variable | Units | Description |
| --- | --- | --- |
| aspect | ° | aspect |
| burned areas | unitless | rasterized burned polygons. 0 when no burned area occurs in that cell, 1 if it does for the day of interest |
| curvature | rad | curvature |
| d2m | K | day's maximum 2 metres dewpoint temperature |
| dem | m | elevation |
| ignition_points | hectares | rasterized fire ignitions. It contains the final hectares of the burned area resulted from the fire |
| lai | unitless | leaf area index |
| lc_agriculture | % | fraction of agriculture in the pixel. 1st Jan of each year has the values of the year |
| lc_forest | % | fraction of forest in the pixel. 1st Jan of each year has the values of the year |
| lc_grassland | % | fraction of grassland in the pixel. 1st Jan of each year has the values of the year |
| lc_settlement | % | fraction of settlement in the pixel. 1st Jan of each year has the values of the year |
| lc_shrubland | % | fraction of shrubland in the pixel. 1st Jan of each year has the values of the year |
| lc_sparse_veagetation | % | fraction of sparse vegetation in the pixel. 1st Jan of each year has the values of the year |
| lc_water_bodies | % | fraction of water bodies in the pixel. 1st Jan of each year has the values of the year |
| lc_wetland | % | fraction of wetland in the pixel. 1st Jan of each year has the values of the year |
| lst_day | K | day's land surface temperature |
| lst_night | K | nights' land surface temperature |
| ndvi | unitless | normalized difference vegetation index |
| population | people/km^2 | population count per year. 1st Jan of each year has the values of the year |
| rh | %/100 | day's minimum relative humidity |
| roads_distance | km | distance from the nearest road |
| slope | rad | slope |
| smi | unitless | soil moisture index |
| sp | Pa | day's maximum surface pressure |
| ssrd | J/m^2| day's average surface solar radiation downwards |
| t2m | K | day's maximum 2 metres temperature |
| tp | m | day's total precipitation |
| wind_speed | m/s | day's maximum wind speed |

</details>


</br> The code used to extract the burned dataset is located in [Portugal_Dataset_Extraction/Extraction_of_Burned_Data](https://github.com/Aser-Abdelfatah/Portugal-Wildfire-Research/tree/main/Portugal_Dataset_Extraction/Extraction_of_Burned_Data), and the code used to extract the non-burned dataset is located in [Portugal_Dataset_Extraction/Extraction_of_Non-burned_Data](https://github.com/Aser-Abdelfatah/Portugal-Wildfire-Research/tree/main/Portugal_Dataset_Extraction/Extraction_of_Non-burned_Data). </br> </br> There are two clustering algorithms used. First is K-means, and the code used along with the visualizations is stored in a Juypter notebook located in [Clustering/K-Means](https://github.com/Aser-Abdelfatah/Portugal-Wildfire-Research/tree/main/Clustering/K-Means). The Legacy folder located in [Clustering/K-Means](https://github.com/Aser-Abdelfatah/Portugal-Wildfire-Research/tree/main/Clustering/K-Means) has old code that is left for reference only. The second clustering algorithm is self-organizing map (SOM). The code is in R and is located in [Clustering/SOM](https://github.com/Aser-Abdelfatah/Portugal-Wildfire-Research/tree/main/Clustering/SOM). There is a knitted pdf file and an R source code. More information on re-producing the SOM is located in the README located inside [Clustering/SOM](https://github.com/Aser-Abdelfatah/Portugal-Wildfire-Research/tree/main/Clustering/SOM).

<\br> There is a code for susceptibility map based on Random Forest located in [Classification/Random_Forest](https://github.com/Aser-Abdelfatah/Portugal-Wildfire-Research/tree/main/Classification/Random_Forest). Further analysis need to be done, however, to optimize the susceptibility map. <\br>

## Recommendations:
- Engineer new annual climatic features computed as the average of the meteorological data over one year before the event
- Use different classification algorithms for the susceptibility map
- Generalize to larger area than Portugal
  

## Reference

<a id="1">[1]</a> https://github.com/Orion-AI-Lab/mesogeos/tree/main
