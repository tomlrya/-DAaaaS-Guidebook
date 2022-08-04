# How to publish and share

(placeholder)
Text...

---

##Best Practices
<br>
###Shapefile is a bad format!
<details>
<summary>Here are several reasons why the Shapefile is a bad format and you should avoid its usage: </summary>

<ul>
<li>No coordinate reference system definition.
<li>It's a multifile format.
<li>Attribute names are limited to 10 characters.
<li>Only 255 attributes. The DBF file does not allow you to store more then 255 attribute fields.
<li>Limited data types. Data types are limited to float, integer, date and text with a maximum 254 characters.
<li>Unknown character set. There is no way to specify the character set used in the database.
<li>It's limited to 2GB of file size. Although some tools are able to surpass this limit, they can never exceed 4GB of data.
<li>No topology in the data. There is no way to describe topological relations in the format.
<li>Single geometry type per file. There is no way to save mixed geometry features.
<li>More complicated data structures are impossible to save. It's a "flat table" format.
<li>There is no way to store 3D data with textures or appearances such as material definitions. 
<li>There is  no way to store solids or parametric objects.
<li>Projections definition. They are incompatible or missing.
Line and polygon geometry type, single or multipart, cannot be reliably determined at the layer level, it must be determined at the individual feature level.
<li>There is no NULL value, it is painful for numeric values
</ul>
</details>

