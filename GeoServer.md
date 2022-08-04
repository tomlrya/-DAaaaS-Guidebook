# GeoServer

GeoServer takes GIS inputs (geoTiff, Shapefiles, Geopackages, Rasters, Mosaics, PostGIS) and processes them into outputs, or services, that are more easily consumed over the web. 


There are three *four* types of services (outputs) in GeoServer.

- **Web Mapping Services (WMS)** provide the map as an image; WMS can be used for both vector and raster data

- **Web Feature Services (WFS)** provide features with their geometry and attributes. GeoJSON is the most common formate of a WFS. However, it can support formats such as shapefiles and CSVs. WFS only support vector data

- **Web Coverage Services (WCS)** are similar to WFS but serve raster data. WCS provide tile services that take large raster data and divide them into tiles that only load in the geographic area in view. Tile services allow the data to be consumed more efficiently online.

- *Web Processing Services (WPS)** provide geoprocessing such as calculations and algorithms. They are essentially geoprocessing tools available online that can write to data locally or on a database. Unfortunately, WPS are not supported out-of-the-box in GeoServer and must be added with an extension.*

!!! note
	
	Only designated people have access to the internal workings of GeoServer.  If you think you require access, please contact your DAaaS *point person*.

## Getting Started

### Log in/Sign on

![geoserver_login](/images/geoserver_login.png){: width=50%}

Once you are logged in, you will see the GeoServer homepage. The left-hand column contains a list of tools you will use to manage the server. The tools are grouped into related categories, such as the About & Status tool group that will give you information about the server. 


![geoserver_tools](/images/geoserver_tools.PNG){: width=50%}

### Orginization of Data
The first tool in the Data group is the Layer Preview. The tool is not part of the hierarchy, but it will give you a list of all the layers available on your GeoServer.

####Workspaces

Click the Workspaces tool from the Data group on the homepage. You will see the Workspaces dialogue. Click the green plus button at the top of the page to add a new Workspace. Give the Workspace a name. 

![geoserver_workspace](/images/geoserver_workspace.PNG){: width=50%}


	- The name should not contain blank spaces
	 
	- The name can be anything unique 
	
	- The name should clearly identify your Project
	 
	- The Workspace will also require Namespace URI
		

####Stores

Click Stores or you can first navigate back to the homepage by clicking the GeoServer icon in the top lefthand corner. Once you have navigated to the list of Stores, click the green plus button to add a new Store. Here you will see a list of all the different inputs that can be loaded on the server.

![geoserver_source](/images/geoserver_source.png){: width=50%}

####Layers

Next, you will add a Layer. Click Layers from the list of tools on the homepage. Click the green plus to add a new Layer. You will choose from which Store you want to add a Layer. Choose the PostGIS Store you just created. A list of Layers that are available in the Store will appear. Select publish next to the Layer. The Edit Layer dialog will appear. You can change the name if you want. You will need to ensure the Coordinate Reference System is correct. GeoServer will try and determine this automatically. You can double-check the coordinate system by loading the data into QGIS. Right-click the feature on the layers pane and navigate to Source. You will next compute the bounding boxes by clicking Compute from data and Compute from native bounds. Click Save. You will see your new feature in the Layers list.

Back on the list of tools, choose the Layer Preview option. You should see the Layer you just created. Click the OpenLayers link in the Common Formats column. A new tab will appear with an OpenLayers map of your data. The data will be symbolized in the default symbology.


####Layer Group

Text

## Symbolizing your Data

GeoServer stores symbology and labels in XML documents called *Styles*. 

**You can create your customized Style in QGIS** by symbolizing and labeling your data and storing the symbology as a **Style Layer Definition file (SDL)**.

!!! note

	You can apply the same Styles file to multiple Layers on the server.


### Creating a Style SLD in QGIS
To do this, load your data into QGIS:

1. Right-click the feature in the Layers pane and select Layer Properties. 
	1. From the Symbology and Labels tabs, you can configure your symbology and labeling to your liking. 
	
2. Click the Style button in the left-hand bottom of the options.
	1. Select Save Style, and you will see the Save Layer Style dialog. 
	2. Use the first dropdown to save the Style as an SDL file somewhere on your local machine.

3. Go back to GeoServer and select the Styles tool from the Data tool group. 
	1. Select the green plus to add a new Style. The New style dialog will appear. 
	2. Give your Style a name and choose the Workspace where you want it to be stored. 
	3. Click the Browse button and navigate to where you stored your SDL file on your local machine. Select the file and click Upload. The XML for your Style will be loaded into the window. 
	4. Click Validate to ensure that there are no validation errors. Click Save.

4. Go to your Layers tool. Select the Layer to which you want to apply the Style. 
	1. Select the Publishing tab at the top of the page. 
	2. Towards the bottom of the page, you will see the Layer Settings and Default Style. 
	3. Select the Style you just created from the list and click Save.