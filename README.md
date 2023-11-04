# Challenge: future housing & development w/ inCitu
## Problem Statement:

Cities like SF are at the forefront of most 21st Century challenges. It notoriously takes longer and costs more to build housing in the city of SF than anywhere else in California, contributing to the state's homelessness crisis and making it hard for workers to live in the area. The city has pledged to facilitate the development of more housing, including a goal of 46,000 units below market rate by 2031. 

Meanwhile, the general public does not have reliable, trustworthy tools to help them envision the future of their urban home. While city planning and development data are technically publicly available, the information is often inaccessible, opaque, and mostly only used by the usual suspects: those who are already in power or motivated to spend hours at lengthy and jargon-laden planning meetings. This can lead to protracted fights over development instead of productive conversations, and crowd out silent majority support for crucial new development, especially affordable housing.

## About inCitu 
At [inCitu](https://www.incitu.us/), we are on a mission to democratize city planning and bring the future of the built environment to life through Augmented Reality. We make open data more actionable, tangible and accessible to all residents, on the ground level. With our mobile AR, anyone can simply scan a QR code to interact with the future of their cities in 3D.

For Accelerate-SF, we will be providing hackers with open planning data from San Francisco. inCitu has cleaned this data and prepared it for you to use in your work. 

We developed a pipeline to turn Building Permits from SF open data into a city-wide AR layer, using 3D generative AI to create location-based AR experiences. Our platform is already active in three US Cities, and we are excited to expand to SF!

As hackers in this challenge, **we are giving you access to multiple stages of our pipeline, which will allow you to generate data, 3D assets, or full AR outputs** <br> for your projects, and help your users imagine what SF would be like if the data about its future was accessible and viewable from everyone’s fingertips.

## Expected Outcomes:
* Highly accessible visualization of proposed and upcoming development projects
* Increase inclusivity, transparency, trust in the planning process
* Streamline permitting and building of new and affordable homes

## We will provide you with
**1. Cleaned and filtered tabular permits data** joined with Building Footprints data that includes the essential information about the future development projects within San Francisco and also the required information to create 3D AR models. 

**2. 3D building models generated from the tabular data** using our technology that are AR deployment ready. 

**3. Access to our API with complete projects** that include: generated 3D models geo-anchored in AR, QR codes, project web map. 
![diagram](https://i.imgur.com/psK8JVh.png)

The API is provided in GraphQL format. A demo query (which includes most relevant entities and fields) can be viewed and run here:
[City Projects Query](https://studio.apollographql.com/sandbox/explorer?endpoint=https%3A%2F%2Fapi.incitu.us%2Fgraphql&explorerURLState=N4IgJg9gxgrgtgUwHYBcQC4QEcYIE4CeABFAJYoED6ADnhAFYJQoDORwAOkkUbQ06wAUAdwAW%2BBOnYlyBKcCKkW8okgCGiFQhxqANsqIcQAZTXcAYnjNkWUCEaIBfJy8cBKdlx49SYL9-VEfx41MDA8BBYWYKIwSKg8UmoUUggkGJYUNRQYaO5vXTSAc3IYOJjdbNLy-JDdFJya7xkKAEk-WqIWCBg8KAQAJSYIPDB2mMhYRFQ2Tk6eQIQYnl7dGMcYgCMYUl0wUiQi2eWiADMICBRaA5Rx%2BdjhBF1dA6KAVSRyPOaebd39w4AFQI1CW9z%2Be1exlEalBJwhAKKAAkEKQiqIUPCdpDDgBZbL4Uh6E6nQojY73HhFOgwJBgcxkvAnHiki54FFojEnDb3OAQOK6ADMYApP28FDhlLOuwQABloFU0syiNZRCNXp4pVSEBBfBz0ZitSqkFA1XgAMJsgEEzVisWFQ7VMF2n6VBplZ0u7x6d1NL08l0Bn5BnhBnk8kCOIA)

For programmatic access, you can use the following endpoint: `https://api.incitu.us/graphql`, and explore the schema.

The main API entities are:
- `Project` - a future development project (can be filtered by `city: "San Francisco"`)
- `Building` - a building that is part of a project
- `Model3D` - a 3D model of a building
- `Anchoring` - a geo-anchoring of a 3D model
- `Document` - a document related to a project; 
also used to link to 2 special documents: `SmartQR` and `qr` which are links to AR/web views of the project


## Example uses
- **Use our cleaned, ready-to-use permits data to generate your own 3D**<br> 
Your 3D output can be either sent through our API to experience it in AR or you can export it to your medium/platform of choice.

  _For example:_ 
  - Use ML to enrich or expand on existing permit data to generate more detailed building models
  - Use ML to create hypothetical data inputs to show what developments would look like if certain zoning/laws were in place
  - Use our cleaned data for any projects relating to housing, development, zoning, or the future of SF
  - Use ML to generate future buildings in 3D, and view them in real scale on site through the inCitu platform


- **Use an export of our generated 3D models in your own projects**<br> 
Use our data and generated buildings to create novel visualizations. 
What are some new ways in which you might use these 3D outputs? 

  _For example:_ 
  - Embed our 3D models into a map based project visualizing data related to climate or any other issue
  - Improve our model exports by adding textures, details, and other characteristics using generative AI
  - Use our models in a futuristic game world   


- **Use our complete output of SF future developments**<br> 
  You can use our full output which includes a web map and QRs leading to geo anchored AR.

  _For example:_
  - Activate a future building site in AR near the hackathon venue using inCitu’s pipeline
  - Imagine other ways to encourage discoverability on the street or online. 
  - How might our AR empower another product or experience? 

## Examples of inCitu activations from Other Cities:

Examples of inCitu activations from Other Cities:
- NYC: 
[Web Map](https://www.incitu.us/map),[Storymap](https://storymaps.arcgis.com/stories/24ab655556494c91aaa799ad6f48d59a),[Tour](https://youtu.be/HDGK7zhIYe4?feature=shared),[Case Study: How we created the most visible rezoning proposal in the history of city planning](https://medium.com/incitu/how-we-created-the-most-visible-rezoning-proposal-in-the-history-of-city-planning-d2235be90ce0)


- Charleston, SC: 
[inCitu launching Augmented Reality experience for Charleston flood protection development](https://www.auganix.org/ar-news-incitu-launching-augmented-reality-experience-for-charleston-flood-protection-development/)

- Washington DC: 
[Video](https://www.instagram.com/incitu_ar/)
