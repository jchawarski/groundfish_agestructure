# groundfish_agestructure
For work done on my M.S. Thesis

This workflow is designed to use federal data fisheries data and create a before-after control-impact analysis of fisheries closures (de-facto MPAs) on the age structure of several groundfish species. 

There are several steps included:

1) Combine station data with biological sampling data (Station.df and Age.df) to assign lat/long

2) Apply age-length keys (probability matrix) from subsampled data (fish that were aged)

3) Subset by species and year and convert into spatial data.

4) Load shapefiles and match projections of point data with area boundaries. 

5) Define the 'Before' and 'After' periods. Based on when the management change took place and temporal balance of the dataset. This is different for each closure.

5) Spatially sample the dataset using discrete geographical boundaries (using readOGR; shapefiles)
      
     a There are two methods I applied here: Distance-based sampling (10km rings away from boundary) and stratified sampling, which is             based on statistical boundaries that are delineated by depth, and latitudinal species distribution. These strata were decided by           NOAA
      
     b Distance bands were created in ArcGIS using the spatial analyst toolbox. I then subsample the 'distance' attribute listed in the             shapefile and break each band into individual shapefiles
      
     c To get the points in each of the discrete distance bands I used the over() function from rgeos or point.in.poly() from spatialEco.
     
     d The location of the points within these boundaries is defined as 'Status'
