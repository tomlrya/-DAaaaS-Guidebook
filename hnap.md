# GeoSpatial Standards - ISO 19115*HNAP

##Metadata Standards

Metadata supports users in locating and accessing their resources, and data consumers in locating and using geodata resources produced by others. 

Metadata includes information about the content, quality, condition, and other characteristics of geodata.  It is necessary to document the temporal and spatial context of your data.

:earth_americas: <b> The DAaaS Geospatial Platform utalizes the following standards: <ins>ISO 19115-2003 HNAP </ins>, GeoDCAT-ap, SDMX. </b>

Standards facilitate the creation, sharing, and general use of geospatial data. Standards are necessary for interoperability between platforms, especially in the cloud environment.

---

## 19115-2003 HNAP


The North American Profile of ISO 19115 - Geographic information - Metadata (HNAP - Metadata), published by the Canadian General Standards Board, identifies the geospatial metadata needed for North America to describe geospatial data, including dataset and dataset series, and related Web services. 
  
This metadata format is a Canadian variant of the North America Profile of ISO 19115 2003, which has a defined XML schema that supports federal government requirements. However, HNAP is not fully compatible with either the ISO or the NAP standards and thus requires unique processing which has been inigrated in the DAaaS Platform.


#### Mandatory Elements
This section provides guidelines for populating the minimum mandatory metadata elements for Government of Canada geospatial datasets.

|Element    | Description|
| --- | ---|
||<b>Section 1: Metadata Information</b>
	|:triangular_flag_on_post: *File Identifier      | Each metadata record shall have a universal unique identifier (UUID)|
	| *Language | Language code and country of the initial metadata language. eng; CAN or fra; CAN        |
	| *Character Set   | Encoding of the metadata record.       |
	| Hierarchy Level    | Level to which the metadata applies. Values typically are "dataset; jeuDonnées" or "series; série".       |
	| Organization Name  | Organization responsible for the metadata.        |
	| Email   | Email of the organisation (general).       |
	| Role   | Responsible partt function        |
	| *Date | Date that the metadata was created or last modified  (date or dateTime type).|
	| *Metadata Standard Name  |   Name of the metadata standard/profile used.     |
	| Code| EPSG code or SR-ORG code.       |
||<b>Section 2: Identification Information</b>|  |
	|Tite| Title of the Data|
	|Date|Date of creation for the data. Repeate for creation, publication and revision.
	|Date Type| Creation, Publication, or Revision|
	|Organization Name| Organisation responsible for the data.|
	|Email|Email of the organisation.|
	|Role|Reponsible party function. Suggestion: pointOfContact; contact|
	|Abstract|Brief narrative summary of the dataset's contents|
	|:triangular_flag_on_post:Status|Development phase of the dataset- see codelist !!DEAD LINK!!
	|Update Frequency|Revision cycle of the data.|
	|:triangular_flag_on_post:Keyword|Codelist. :triangular_flag_on_post:-link-:triangular_flag_on_post:
	|*Title |Thesaurus title |
	|*Date|Thesaurus creation date |
	|*Date Type | Date type |
	|*Date|Thesaurus publication date |
	|*Date Type | Date type |
	|*Orginazation Name | Name of the organisationresponsible for the thesaurus |
	|*Role |Role of the organization responsible for the thesaurus. |
	|:triangular_flag_on_post:*Use Limitation |:triangular_flag_on_post:|
	|:triangular_flag_on_post:*Access Constraints | :triangular_flag_on_post: |
	|:triangular_flag_on_post:*User Constraints | :triangular_flag_on_post: |
	|Spatial Representation Type|Spatial representation type of the data. (vector, grid, textTable, tin, stereoModel, video)|
	|Language|Language of the data (usually eng; CAN or fra; CAN)|
	|Topic Catagory| Main theme (English only) of the data. (farming, biota, boundaries, climatologyMeteorologyAtmosphere, economy, elevation, environment, geoscientificInformation, health, imageryBaseMapsEarthCover, intelligenceMilitary, inlandWaters, location, oceans, planningCadastre, society, structure, transportation, utilitiesCommunication)|
	|West Bound Longitude|Geographic Bounding Box|
	|East Bound Longitude|Geographic Bounding Box|
	|South Bound Latitude|Geographic Bounding Box|
	|North Bound Latitude|Geographic Bounding Box|
	|Begin Date|Beginning or Start date of the time period that a particular dataset covers or describes|
||<b>Section 3: Distribution Information</b>| |	
	|Name (file format)|Format of the data distributed|
	|Version|Version number or date of the format (or: uknown)|
	|Orginazation Name|Organisation responsivle for the distribution|
	|Email Address|Email of the organisation responsivle for the distribution|
	|Role|Reponsible party function; Suggestion: distributor; distributeur|
||<b>Section 4: Web Map Service</b> (if necessary)| |
	|Linkage (Service URL)|For a OGC:WMS service type, the format must conform to: "a GetCapabilities request with non-standard parameters (mandatory :  “LAYERS=<layername>”, optional : ""LEGEND_FORMAT=legend_format>"" and ""FEATURE_INFO_TYPE=<featureInfoType>"") :"|
	|Protocol|The value must conform to : OGC:WMS or ESRI REST: Map Service|
	|Name|The name of the resource being described.|
	|Description|The format must conform to: ContentType;Format;Lang(,Lang,Lang) where: ContentType:  Web Service; Format :  WMS or ESRI REST; Lang : eng, fra, zxx (for no linguistic content e.g. imagery) or the appropriate code from ISO 639-2/T.; List the data language(s) , seperated by comma if more than one. |

<sup>    * Automatically generated by DAaaS Catalog </sup>


[North American Profile of ISO19115:2003 Register - Codelists](http://nap.geogratis.gc.ca/metadata/register/codelists-eng.html#IC_109)

</p>
<br>

---

## GeoDCAT-ap

GeoDCAT is a vocabulary designed to facilitate interoperability between catalogs.  It increases discoverability and will enable federalization of datasets.  GeoDCAT does not replace 19115; its purpose is to enhance it for catalogs.  
 
GeoDCAT is for the exchange of descriptions of geospatial datasets, dataset series and services. It provides an RDF syntax binding for the union of all metadata elements defined in the core profile 19115.
 
The DAaaS Platform automatically coverts your ISO 19115 metadata file into GeoDCAT.


---

##SDMX

SDMX 3.0 ...

---

## Learn More
List of resources to learn more

[DCAT Standard](https://www.w3.org/TR/vocab-dcat/)

[Government of Canada Geospatial Standards(Internal GC Only)](http://www.gcpedia.gc.ca/wiki/Federal_Geospatial_Platform/Policies_and_Standards/Catalogue/Release/Appendix_B_Guidelines_and_Best_Practices/Guide_to_Harmonized_ISO_19115:2003_NAP)

[TBS: Policies, directives, standards and guidelines](https://www.tbs-sct.gc.ca/pol/doc-eng.aspx?id=16553)

[Digital Geospatial Metadata (NRCAN)](https://www.nrcan.gc.ca/earth-sciences/geomatics/canadas-spatial-data-infrastructure/standards-policies/8912)