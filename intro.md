# A Simple Introduction to Geospatial Analysis


<p align='center'>
<img src="https://i.ibb.co/TrGQv9f/intro.png" alt="html picture">
</p>
__Geospatial analysis is concerned with the quantitative location of important features, known as phenomena.__
  
Geospatial data is data about phenomena that have a location on the surface of the earth. The location may be static (ex- the location of a road, a disaster event, citizens living in poverty), or dynamic (ex- a moving vehicle or pedestrian, the spread of COVID)
<br>

A GIS (Geospatial Information System) helps us analyze spatial relationships and patterns amongst these phenomena. It is particularly useful for visualizing spatial data and reporting results of analysis.

GIS' are composed of both hardware and software components. Due to the large volumes of spatial data and the need to display values on the fly, GIS hardware often have large storage capacities, fast computing speed, and powerful memory. <b>DAaaS has been designed meet these users neeeds.</b>

---

###About Spatial Data
Spatial data are data types (files, databases, web services) that encode geographic information for use in location-aware applications.
There are two types:

<ol>
	<li> <b>Vector data</b>
		<ul>
		<li>points (x, y, z coordinates)
		<li>lines (roads, networks) 
		<li>polygons (areas).
		</ul></li>

	<li> <b>Raster data</b>
		<ul>
		<li> images or grids of digital values; eg. satellite imagery.
		</li></ul>
</ol>


A <b>spatial database</b> — also known as a “<b>geodatabase</b>” — is built to capture and store the points, lines, and polygons.


###GIS Vocabulary

|Term||Description|
|----||----|
|Base Map||GIS data and/or imagery that form the background setting for a map |
|Coordinates||Values represented by the letters x, y, z [or m (measure)], that define a position within a spatial reference|
|DCAT, geoDCAT-ap||Metadata standrad to make spatial datasets, dataset series, and services searchable on general data catalogs|
|EO, Earth Observation||Information about the planet Earth gathered via remote-sensing technologies and by ground-based techniques (ex- satellite or drone imagery|
|ETL||Procedure of copying data from sources into a destination system which represents the data differently from the source or in a different context than the source|
|Generalization||Method used in GIS to reduce detail in data (for privacy and/or visualizing)|
|Geocode||The process of identifying a location by one or more attributes from a layer. |
|HNAP||HNAP-Canada is a profile on Harmonized North American Profile which itself is a profile on ISO19139 (ISO 19115*)|
|Layer||Thematic data described and stored in a map library. Layers act as transparencies that can be laid atop one another for viewing or spatial analysis. |
|OGC||Open Geospatial Consortium- Open Source champion.....|
|Term||Description|
|Shapefile|| vector data storage format for storing the location, shape, and attributes. It is stored in a set of 4 related files and contains one feature class. *shapefiles should be avoided in production*|
|Term||Description|
|WMS||specifications that provides uniform access by Web clients to maps rendered by map servers on the Internet|
|WFS||specifications that standardizes data manipulation and map display on the Internet|
|Term||Description|

