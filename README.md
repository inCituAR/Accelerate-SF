# inCitu x Accelerate-SF
at [inCitu](https://www.incitu.us/), we are on a mission to democratize city planning and bring the future of the built environment to life through Augmented Reality. 
We make open data more actionable, tangible and accessible to all residents, on the ground level in the streets. 
With our Ai powered generative technology channeled into mobile AR, anyone can simply scan a QR code to interact with the future of their cities in 3D.

# Working with SF Open Data

## [Permits and Application Data](https://data.sfgov.org/Housing-and-Buildings/Building-Permits/i98e-djp9)
The main source of future projects and necessary attributes for these project to create the AR models. 

### Permits Type Definition: this is the where work application
For the purpose of visualizing the future development in the city, only a subset of the permit is relevant to our purpose. This attribute could be a useful filter to narrow down the relevant projects.
Suggested types to consider are “new construction”, “new construction wood frame”. 

### Current Status Date/Filed Date/Issued Date: 
A search on Google Street View might reveal some projects in the datasets are already finished even when their permits status is not updated to “complete”. Something to consider is to control the universe of data 

### Proposed Use
Building type is a required input for model generation. The values from the source data will need to be cast into one of the few accepted types that our backend schema defined. Please check the data dictionary for what those accepted values are. 

### Number of Proposed Stories
The number of floors the proposed building would have. A required attribute for model generation purposes. 
Description: this would need to be the source of a couple of key attributes the AR model generation pipeline would depend on. This would be a textual analysis exercise and extract as much and also as accurate information as possible.
When the building type is ambiguous or not specified in the attributes mentioned above. Then this could be a supplemental source to generate the building type attribute. 

### [Building Footprints](https://data.sfgov.org/Geographic-Locations-and-Boundaries/Map-of-Building-Footprints/xy57-fey9)
Footprints data need to be joined with the other attributes data in order to create AR models and also to be geo-anchored their future sites.  
Shape: the geometry field which would need to be exported to geojson for model generation

This is currently a multipolygon from the source data. In order to have a successful generation of AR models from our pipeline. This would need to be converted to a Polygon. You might use something like ST_ExteriorRing to do the conversion.
Anchor point calculation would also depend on the footprint geometry. Something like ST_DumpPoints might help create the collections of points that would be iterated through to . See more explanations about anchor points in the notes below. 

### [Sidewalks](https://data.sfgov.org/Transportation/Map-of-Sidewalk-Widths/ygcm-bt3x)
Sidewalk data is relevant for the anchor calculations for the AR models. Please see more detailed notes below on how anchor calculations are done. The elevation point of the sidewalk is part of the output dataset from the open data pipeline. 
Shape: the geometry is the feature used to calculate the distance from each anchor points candidates and determine which is closest to the sidewalk. The logics could be summarized as followed
First, pick a closest sidewalk to the project by comparing to all sidewalks to the project centroid
Then, an anchor point is picked from the footprints geometry that is closest to the closest sidewalk

## Additional Notes on anchor points

## Finding the nearest point to anchor the AR model
After multiple on site tests we found out that it is best if we set the AR anchor point to a corner of the footprint closest to the sidewalk. To make these calculations part of the automation, we created some logic that gets the Sidewalk polygon data and finds the closest Sidewalk, then by iteration through footprint polygon data we compare the distances between polygon points and sidewalk. The elevation point is also picked from the nearest sidewalk after the anchor point is selected. Then, the elevation point is defined as the point on the sidewalk that is closest to the building anchor point. Then using latitude and longitude we can query the elevation data from https://epqs.nationalmap.gov




