# G3P_IGRAC
Codes and workflow to process G3P.nc files and in-situ groundwater data

Under the G3P project, codes were generated to process G3P.nc files and in-situ groundwater data. The objective was to generate area-average time series of groundwater stoarge anomalies from G3P and area-average time series of in-situ groundwater storage anomalies (GWSA) or groundwater level anomalies (GWLA) to compare them using Pearson correlation and see how similar they are.

For that purpose, 4 jupyter notebooks are going to be used in a certain order

 1. "insitu_GWSA_temporal_demo" or "insitu_GWLA_temporal_demo"
 
 This notebook is used first to calculate in-situ GWSA or GWLA. The input data is:
  - WATERLEVEL_demo: In-situ groundwater level time series (depth to groundwater in m) in the format: SiteNo / date / waterlevel
  - all_coordinates_demo: List of available sites where groundwater levels were measured, their name, coordinates (lon,lat), and if available whether they are in a confined or unconfonied situation.
  Every step is specified in the notebook. Both of the notebooks have an intermediate step to be carried out in QGIS, and detailed in the documents: "qgis_GWSA_demo.doc" and "qgis_GWSA_demo.doc". 
  
  The output is either in-situ GWSA or GWLA, in the form of:
   - "longdf_alldata_2002_2016_demo.xlsx" for in-situ GWSA
   - "longdf_alldata_2002_2016_GWLA_demo.xlsx" for in-situ GWLA
 
 2. "g3p_newperiod_demo"
 
 This notebook is used when the period of evaluation or analysis to be done with G3P is different from the original period with which G3P comes.
 
 The input data is:
  - "G3P_GWSA_V1.5_0.5deg_M_200204_202012.nc" or the latest version of G3P
 
 The output data is:
  - "G3P_GWSA_V1.5_0.5deg_M_200204_202012_mean_base_2002_2016.nc"
  - "G3P_GWSA_LA_hyd_V1.5_0.5deg_M_200204_202012_mean_base_2002_2016.nc"
  - "G3P_GWSA_LA_grav_V1.5_0.5deg_M_200204_202012_mean_base_2002_2016.nc",
  
  when the new period is from 2002 to 2016. These three datasets are used as input G3P for the calculation of area-average GWSA.
  
  3. "g3pGWSA_vs_insituGWSA_GWLA_demo"
  
  This notebook is used to calculate the area-average G3P GWSA time series and compare it with in-situ GWSA or GWLA.
  The input data is:
   - "G3P_GWSA_V1.5_0.5deg_M_200204_202012.nc" --> to get uncertainties
   - "G3P_GWSA_V1.5_0.5deg_M_200204_202012_mean_base_2002_2016.nc" --> to get GWSA
   - "G3P_GWSA_LA_hyd_V1.5_0.5deg_M_200204_202012_mean_base_2002_2016.nc" --> to get GWSA_LA_hyd
   - "G3P_GWSA_LA_grav_V1.5_0.5deg_M_200204_202012_mean_base_2002_2016.nc"  --> to get GWSA_LA_grav
   - "alternative_area_50x50.shp" --> .shp polygon of aquifer or polygon containing the available boreholes
   - "longdf_alldata_2002_2016_demo.xlsx" --> if in-situ GWSA is calculated
   - "longdf_alldata_2002_2016_GWLA_demo.xlsx" --> if in-situ GWLA is calculated
