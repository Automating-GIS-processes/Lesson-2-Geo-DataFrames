---
anaconda-cloud: {}
---

# Introduction to Pandas and Geopandas

### Topics

1. What are Pandas or Geopandas -modules
2. Data processing in Pandas
3. Working with spatial data using Geopandas

### Sources

These materials are partly based on [Pandas introductory tutorial](http://pandas.pydata.org/pandas-docs/version/0.15.2/10min.html#min) 
and Geopandas documentation.

## What are Pandas or Geopandas -modules?

_Overview of the modules and why are they good._

## Data processing in Pandas



## Working with spatial data using Geopandas

[Geopandas](http://geopandas.org/#description) is a Python module that extends the functionalities of [Pandas](http://pandas.pydata.org/) 
data analysis library (that takes advantage of [numpy](http://www.numpy.org/) module). Geopandas makes possible to work with spatial data 
such as Shapefiles. It is also possible to work with rasters using geopandas with [rasterio](https://github.com/mapbox/rasterio) module 
(see [example](http://gis.stackexchange.com/questions/151339/rasterize-a-shapefile-with-geopandas-or-fiona-python)).

### Data I/O (in / out)

#### Reading a Shapefile

Spatial data can be read easily with geopandas using `gpd.from_file()` -function:

```python
>>> %matplotlib notebook
>>> # Import necessary modules
... import geopandas as gpd
>>> import matplotlib.pyplot as plt
...
>>> # Set filepath
... fp = r"C:\HY-Data\HENTENKA\Data\AutoGIS16\Data\DAMSELFISH_distributions.shp"
...
>>> # Read file using gpd.read_file()
... data = gpd.read_file(fp)
...
>>> # Let's see what we got
... # head() -function prints the first 5 rows by default
... data.head()
              binomial category  \
0   Stegastes leucorus       VU   
1   Stegastes leucorus       VU   
2   Stegastes leucorus       VU   
3  Chromis intercrusma       LC   
4  Chromis intercrusma       LC   

                                            citation      class_name compiler  \
0  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   
1  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   
2  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   
3  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   
4  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   

  dist_comm     family_nam genus_name  \
0      None  POMACENTRIDAE  Stegastes   
1      None  POMACENTRIDAE  Stegastes   
2      None  POMACENTRIDAE  Stegastes   
3      None  POMACENTRIDAE    Chromis   
4      None  POMACENTRIDAE    Chromis   

                                            geometry     id_no  ...  origin  \
0  POLYGON ((-115.6437454219999 29.71392059300007...  183963.0  ...       1   
1  POLYGON ((-105.589950704 21.89339825500002, -1...  183963.0  ...       1   
2  POLYGON ((-111.159618439 19.01535626700007, -1...  183963.0  ...       1   
3  POLYGON ((-80.86500229899997 -0.77894492099994...  183793.0  ...       1   
4  POLYGON ((-67.33922225599997 -55.6761029239999...  183793.0  ...       1   

  phylum_nam rl_update seasonal  source   species_na  subpop  subspecies  \
0   CHORDATA    2012.1        1    None     leucorus    None        None   
1   CHORDATA    2012.1        1    None     leucorus    None        None   
2   CHORDATA    2012.1        1    None     leucorus    None        None   
3   CHORDATA    2012.1        1    None  intercrusma    None        None   
4   CHORDATA    2012.1        1    None  intercrusma    None        None   

  tax_comm  year  
0     None  2010  
1     None  2010  
2     None  2010  
3     None  2010  
4     None  2010  

[5 rows x 24 columns]
```

 - Let's see how our data looks like on a map. If you just want to explore your data on a map, you can use `.plot()` -function in geopandas that creates a simple map out of the data (uses matplotlib as a backend):

```python
>>> # Draw a simple map out of the data
... data.plot()
<IPython.core.display.Javascript object>
<IPython.core.display.HTML object>
```

#### Writing a Shapefile

We can select for example 50 rows of the input data and write those into a new Shapefile by first
<a href="http://pandas.pydata.org/pandas-docs/stable/indexing.html" target="_blank">selecting the data using pandas functionalities</a> and then writing the selection with `gpd.to_file()` -function:

```python
>>> # Create a output path for the data
... out = r"C:\HY-Data\HENTENKA\Data\DAMSELFISH_distributions_SELECTION.shp"
...
>>> # Select first 50 rows
... selection = data[0:50]
...
>>> # Print the head of our selection
... print(selection.head())
...
>>> # Write those rows into a new Shapefile (the default output file format is Shapefile)
... selection.to_file(out)
   ORIG_FID             binomial category  \
0         0   Stegastes leucorus       VU   
1         0   Stegastes leucorus       VU   
2         0   Stegastes leucorus       VU   
3         1  Chromis intercrusma       LC   
4         1  Chromis intercrusma       LC   

                                            citation      class_name compiler  \
0  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   
1  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   
2  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   
3  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   
4  International Union for Conservation of Nature...  ACTINOPTERYGII     IUCN   

  dist_comm     family_nam genus_name  \
0      None  POMACENTRIDAE  Stegastes   
1      None  POMACENTRIDAE  Stegastes   
2      None  POMACENTRIDAE  Stegastes   
3      None  POMACENTRIDAE    Chromis   
4      None  POMACENTRIDAE    Chromis   

                                            geometry  ...   rl_update  \
0  POLYGON ((-115.6437454219999 29.71392059300007...  ...      2012.1   
1  POLYGON ((-105.589950704 21.89339825500002, -1...  ...      2012.1   
2  POLYGON ((-111.159618439 19.01535626700007, -1...  ...      2012.1   
3  POLYGON ((-80.86500229899997 -0.77894492099994...  ...      2012.1   
4  POLYGON ((-67.33922225599997 -55.6761029239999...  ...      2012.1   

  seasonal shape_Area  shape_Leng source   species_na subpop  subspecies  \
0        1  28.239363   82.368856   None     leucorus   None        None   
1        1  28.239363   82.368856   None     leucorus   None        None   
2        1  28.239363   82.368856   None     leucorus   None        None   
3        1  87.461539  729.012180   None  intercrusma   None        None   
4        1  87.461539  729.012180   None  intercrusma   None        None   

   tax_comm  year  
0      None  2010  
1      None  2010  
2      None  2010  
3      None  2010  
4      None  2010  

[5 rows x 27 columns]
```

### Creating geometries in Geopandas

Geopandas takes advantage of Shapely's geometric objects. Geometries are stored in a column called *geometry* that is a default column name for storing geometric information in geopandas.

 - Let's print the first 5 rows of the column 'geometry':

```python
>>> # It is possible to use only specific columns by specifying the column name within square brackets []
... data['geometry'].head()
0    POLYGON ((-115.6437454219999 29.71392059300007...
1    POLYGON ((-105.589950704 21.89339825500002, -1...
2    POLYGON ((-111.159618439 19.01535626700007, -1...
3    POLYGON ((-80.86500229899997 -0.77894492099994...
4    POLYGON ((-67.33922225599997 -55.6761029239999...
Name: geometry, dtype: object
```

Since spatial data is stored as Shapely objects, **it is possible to use all of the functionalities of Shapely module** that we practiced earlier.

 - Let's print the areas of the first 5 polygons:

```python
>>> # Make a selection that contains only the first five rows
... selection = data[0:5]
```

 - We can iterate over the selected rows using a specific `.iterrows()` -function in (geo)pandas:

```python
>>> for index, row in selection.iterrows():
...     # Calculate the area of the polygon
...     poly_area = row['geometry'].area
...     # Print information for the user
...     print("Polygon area at index {0} is: {1:.3f}".format(index, poly_area))
Polygon area at index 0 is: 19.396
Polygon area at index 1 is: 6.146
Polygon area at index 2 is: 2.697
Polygon area at index 3 is: 87.461
Polygon area at index 4 is: 0.001
```

```python

<IPython.core.display.Javascript object>
<IPython.core.display.HTML object>
```
