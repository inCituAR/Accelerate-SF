# Challenge: future housing & development w/ inCitu
## Problem Statement:

Cities like SF are at the forefront of most 21st Century challenges. It notoriously takes longer and costs more to build housing in the city of SF than anywhere else in California, contributing to the state's homelessness crisis and making it hard for workers to live in the area. The city has pledged to facilitate the development of more housing, including a goal of 46,000 units below market rate by 2031. 

Meanwhile, the general public does not have reliable, trustworthy tools to help them envision the future of their urban home. While city planning and development data are technically publicly available, the information is often inaccessible, opaque, and mostly only used by the usual suspects: those who are already in power or motivated to spend hours at lengthy and jargon-laden planning meetings. This can lead to protracted fights over development instead of productive conversations, and crowd out silent majority support for crucial new development, especially affordable housing.

# About inCitu 
At [inCitu](https://www.incitu.us/), we are on a mission to democratize city planning and bring the future of the built environment to life through Augmented Reality. We make open data more actionable, tangible and accessible to all residents, on the ground level. With our mobile AR, anyone can simply scan a QR code to interact with the future of their cities in 3D.

For Accelerate-SF, we will be providing hackers with open planning data from San Francisco. inCitu has cleaned this data and prepared it for you to use in your work. 

We developed a pipeline to turn Building Permits from SF open data into a city-wide AR layer, using 3D generative AI to create location-based AR experiences. Our platform is already active in three US Cities, and we are excited to expand to SF!

As hackers in this challenge, **we are giving you access to multiple stages of our pipeline, which will allow you to generate data, 3D assets, or full AR outputs** for your projects, and help your users imagine what SF would be like if the data about its future was accessible and viewable from everyone’s fingertips.

## Expected Outcomes:
* Highly accessible visualization of proposed and upcoming development projects
* Increase inclusivity, transparency, trust in the planning process
* Streamline permitting and building of new and affordable homes

## Potential Project Ideas
* Use Machine Learning and open data to generate future buildings in 3D and use them in your projects
* Use our data and generated buildings to create novel visualizations with AI
* Use AI to enrich or expand on existing permit data to generate more detailed building models.
* Use AI to create hypothetical data inputs to show what developments would look like if certain zoning/laws were in place
* Using our cleaned data for any projects relating to housing, development, zoning, or the future of SF
* Activate a future building site in AR near the hackathon venue using inCitu’s pipeline

## Similar/Existing Project examples
[Visualize the Wallis Annenberg Wildlife Crossing with New Snapchat Lens](https://annenberg.org/news/visualize-the-wallis-annenberg-wildlife-crossing-with-new-snapchat-lens/)
[Buffalo residents see the future of Ralph Wilson Park Pedestrian Bridge in Augmented Reality!](https://medium.com/incitu/buffalo-residents-see-the-future-of-ralph-wilson-park-pedestrian-bridge-in-augmented-reality-bf32203f83f3)
[The future of NYC is revealed through Augmented Reality](https://storymaps.arcgis.com/stories/24ab655556494c91aaa799ad6f48d59a)
[How we created the most visible rezoning proposal in the history of city planning](https://medium.com/incitu/how-we-created-the-most-visible-rezoning-proposal-in-the-history-of-city-planning-d2235be90ce0)


### Working with SF Open Data

### [Permits and Application Data](https://data.sfgov.org/Housing-and-Buildings/Building-Permits/i98e-djp9)
The main source of future projects and necessary attributes for these project to create the AR models. 

### 1. Permits Type Definition: 
This is the where work application 
* For the purpose of visualizing the future development in the city, only a subset of the permit is relevant to our purpose. This attribute could be a useful filter to narrow down the relevant projects.
* Suggested types to consider are “new construction”, “new construction wood frame”. 

### 2. Current Status Date/Filed Date/Issued Date: 
A search on Google Street View might reveal some projects in the datasets are already finished even when their permits status is not updated to “complete”. Something to consider is to control the universe of data. 

### 3. Proposed Use
Building type is a required input for model generation. The values from the source data will need to be cast into one of the few accepted types that our backend schema defined. Please check the data dictionary for what those accepted values are. 

### 4. Number of Proposed Stories
The number of floors the proposed building would have. A required attribute for model generation purposes. 

### 5. Description
This would need to be the source of a couple of key attributes the AR model generation pipeline would depend on. This would be a textual analysis exercise and extract as much and also as accurate information as possible. When the building type is ambiguous or not specified in the attributes mentioned above. Then this could be a supplemental source to generate the building type attribute. 

## [Building Footprints](https://data.sfgov.org/Geographic-Locations-and-Boundaries/Map-of-Building-Footprints/xy57-fey9)
Footprints data need to be joined with the other attributes data in order to create AR models and also to be geo-anchored their future sites.  
Shape: the geometry field which would need to be exported to geojson for model generation. This is currently a multipolygon from the source data. In order to have a successful generation of AR models from our pipeline. This would need to be converted to a Polygon. You might use something like ST_ExteriorRing to do the conversion. Anchor point calculation would also depend on the footprint geometry. Something like ST_DumpPoints might help create the collections of points that would be iterated through to. See more explanations about anchor points in the notes below. 


