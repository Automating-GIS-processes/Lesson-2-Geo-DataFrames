# Data analysis using Pandas and Geopandas

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

Spatial data can be read easily with geopandas using *gpd.from_file()* function:

 ```python
    # Import necessary modules
    import geopandas as gpd   # geopandas is usually shortened as gpd

    # Set filepath
    fp = r"C:\HY-Data\HENTENKA\Data\DAMSELFISH_distributions.shp"

    # Read file using gpd.read_file()
    data = gpd.read_file(fp)

    # Let's see what we got --> print the 'head' of the file (first 5 rows)
    data.head()
 ```
 
### Writing a Shapefile

We can select for example 50 rows of the input data and write those into a new Shapefile by first
<a href="http://pandas.pydata.org/pandas-docs/stable/indexing.html" target="_blank">selecting the data using pandas functionalities</a> 
and then writing the selection with *gpd.to_file()* function:
