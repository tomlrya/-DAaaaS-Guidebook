# What is AAW
The [Advanced Analytics Workspace](https://analytics-platform.statcan.gc.ca/covid19) (AAW) provides emerging state-of-the-art open source analytics and artificial intelligence tools, and compute capacity for modern data science workloads.
<br/>
<br/>
# Getting Started in AAW
Using Jupyter Notebooks in AAW allows users to connect to the ArcGIS Enterprise Portal using various python APIs. See [Getting Started](https://statcan.github.io/daaas/en/) in AAW and the use of [Jupyter Notebooks](https://statcan.github.io/daaas/en/1-Experiments/Jupyter/) within the space.   
<br/>
# Connecting to ArcGIS Enterprise Portal using ArcGIS API
## Logging into the Portal
Once the Jupyter Notebook is set up in the AAW environment, follow the code example below to get familiar with basic commands to access content on the ArcGIS Enterprise Portal. 
<br/>
<br/>
Begin by pasting ```conda install -c esri arcgis``` into the Notebook and click run. This will allow you to easily install libraries into your Python environment.
<br/>
Import the necessary libraries that you will need in the Notebook.
```python
from arcgis.gis import GIS
from arcgis.gis import Item
from IPython.display import display
```
Your project group will be provided with a Client ID upon onboarding which will be used to connect to the ArcGIS Enterprise Portal. Paste the Client ID inbetween the quoatations <br/>```client_id=' '```. 
```python
gis = GIS("https://geoanalyticsdev.cloud.statcan.ca/portal", client_id=' ')
print("Successfully logged in as: " + gis.properties.user.username)
```
The output will redirect you to a web page where you can login to the Portal using the StatCan Azure Login option. After successful login, you will recive a code to sign in using SAML. Paste this code into the output. 

![OAuth2 Approval](images/OAuth2Key.png)

## Display user information
Using the 'me' function, we can display various information about the user logged in.\
```python
me = gis.users.me
username = me.username
description = me.description
display(me)
```
## Search for Content
Search for the content you have hosted on the DAaaS Geo Portal. Using the 'me' function we can search for all of the hosted content on the account. There are multiple ways to search for content. Two different methods are outlined below.
###Search all of your hosted itmes in the DAaaS Geo Portal.
```python
my_content = me.items()
my_content
```
### Search for specific content you own in the DAaaS Geo Portal.
This is similar to the example above, however if you know the title of they layer you want to use, you can save it as a function.
```python
my_items = me.items()
for items in my_items:
    print(items.title, " | ", items.type)
    if items.title == "Flood in Sorel-Tracy":
        flood_item = items
        
    else:
        continue
print(flood_item)
```

### Search all content you have access to, not just your own.
```python
flood_item = gis.content.search("tags: flood", item_type ="Feature Service")
flood_item
```

##Get Content to Use in the Jupyter Notebook
We need to get the item from the DAaaS Geo Portal in order to use it in the Jupyter Notebook. This is done by providing the unique identification number of the item you want to use. Three examples are outlined below, all accessing the identical layer.
```python
item1 = gis.content.get(my_content[5].id) #from searching your content above
display(item1)

item2 = gis.content.get(flood_item.id) #from example above -searching for specific content
display(item2)

item3 = gis.content.get('edebfe03764b497f90cda5f0bfe727e2') #the actual content id number
display(item3)
```

##Perform Analysis
Once the layers are brought into the Jupyter notebook, we are able to perform similar types of analyis you would expect to find in a GIS software such as ArcGIS. There are many modules containing many submodels of which can perfrom multiple types of analyses.
<br/>

Using the arcgis.features module, import the use_proximity submodule ```from arcgis.features import use_proximity```. This submodule allows us to '.create_buffers' - areas of equal distance from features. Here, we specify the layer we want to use, distance, units, and ouput name (you may also specify other chracteristics such as field, ring type, end type, and others). By specifying an output name, after running the buffer command, a new layer will be automatically uploaded into the DAaaS GEO Portal containg the new feature you just created.
<br/>

```python
buffer_lyr = use_proximity.create_buffers(item1, distances=[1], 
                                          units = "Kilometers", 
                                          output_name='item1_buffer')

display(item1_buffer)
```

##Update Items
By getting the item as we did similar to the example above, we can use the '.update' function to update exisiting item within the DAaaS GEO Portal. We can update item properties, data, thumbnails, and metadata.
```python
item1_buffer = gis.content.get('c60c7e57bdb846dnbd7c8226c80414d2')
item1_buffer.update(item_properties={'title': 'Enter Title'
									 'tags': 'tag1, tag2, tag3, tag4',
                                     'description': 'Enter description of item'}
```

##Visualize Your Data on an Interactive Map
### ipyleaflet Library
In this example we will use the library 'ipyleaflet' to create an interactive map. This map will be centered around Tornoto, ON. The data being used will be outlined below.
Begin by pasting ```conda install -c conda-forge ipyleaflet``` allowing you to install ipyleaflet libraries in the Python environment.
<br/>
Import the necessary libraries.
```python
import ipyleaflet 
from ipyleaflet import *
import json
import os
```
Now that we have imported the aipyleaflet module, we can create a simple map by specifying the latitude and longitude of the location we want, zoom level, and basemap [(more basemaps)](https://ipyleaflet.readthedocs.io/en/latest/map_and_basemaps/basemaps.html). Extra controls have been added such as layers and scale.
```python
toronto_map = Map(center=[43.69, -79.35], zoom=11, basemap=basemaps.Esri.WorldStreetMap)

toronto_map.add_control(LayersControl(position='topright'))
toronto_map.add_control(ScaleControl(position='bottomleft'))

toronto_map
```
<br/>
**Getting the Data from the Portal**
<br/>

It is important to note that this mapping widget does not interact with the DAaaS Geospatial Portal directly. We will have to export our layers that we created into something the ipyleaflet widget will understand. To do this we will export into a GeoJSON data type.
<br/>

First, we have to export the item as 'GeoJson' then download the item from the portal and specify a new folder we want to add the item to.
```python
item_export = item1_buffer.export('item1_buffer_JSON', export_format='GeoJson', tags='tag1, tag2, tag3')

item_download = item_export.download("item1_JSON")
```
Next, add the layer to the ipyleaflet interactive map.
```python
with open('item1_JSON/item1_buffer_JSON.geojson') as f:
    data1 = json.load(f)

item1_buffer_lyr = GeoJSON(
    data=data,
    style ={
        'opacity': 1,
        'color': '#0000FF',   # Hex Code
        'fillColor': 'red',   # Text
        'fillOpacity': 0.2,
        'weight': 1},
    hover_style={
        'color': 'white',
        'fillOpacity': 0.5
    }
)

toronto_map.add_layer(item1_buffer_lyr)
```
By clicking run on the code, the layer is automatically updated on the interactive map above and there is no need to create a seprate map.
![ipyleaflet](images/ipyleaflet_map.png)

###leafmap Library 
The leafmap library is similair to the ipyleaflet library as seen above in a way that it lets you visualize data on an interactive map. It also comes with a suite of tools that allow you to change basemaps, upload data, perfrom analysis, and many other functions.
Begin by pasting ```conda install leafmap -c conda-forge``` allowing you to install leafmap libraries in the Python environment.
Import the leafmap library.
```python
import leafmap
```
Set up an initial map.
```python
toronto_map2 = leafmap.Map(center=[43.69, -79.35], zoom=11)
toronto_map2
```
Again, we will need to use GeoJSON data. We are not performing any analysis here as it was already performed. We are simply calling on the GeoJSON data by specifying its path in the Jupyter Notebook. We also have a function that will assing each polygon with a random color (in our case, either red or blue).
```python
data2 = 'item1_JSON/item1_buffer_JSON.geojson'

hover_style={
        'color': 'white',
        'fillColor': 'red',
        'fillOpacity': 0.5
}

import random

def random_color(feature):
    return {
        'color': 'black',
        'fillColor': random.choice(['red', 'blue']),
    }

toronto_map2.add_geojson(data2, layer_name=data2_name, style_callback=random_color, hover_style=hover_style)
```
![leafmap](images/leafmap_map.png)

###leafmap Libarary with Kepler Extension
This will provide the user with many more customization options while needing the least amount of code compared the other mapping widgets demosntrated above.
Begin by pasting ```pip install keplergl``` allowing you to install the extension to the leafmap widget in the Python environment.
Import the leafmap library and extension along with the geopandas library.
```python
import leafmap.kepler as leafmap
import geopandas as gpd
```

Set up and import data to the interactive map.
```python
toronto_map3 = leafmap.Map(center=[43.69, -79.35], zoom=10)

gdf = gpd.read_file("item1_JSON/item1_buffer_JSON.geojson")
toronto_map.add_gdf(gdf, layer_name='Police Buffer')

toronto_map
```
![leafmap keplergl extension](images/leafmap_keplergl_map.png)