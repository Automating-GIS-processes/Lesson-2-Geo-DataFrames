# Introduction to Pandas and Geopandas

### Topics

1. What are Pandas or Geopandas -modules
2. Data processing in Pandas
3. Working with spatial data using Geopandas

### Sources

These materials are partly based on [Pandas introductory tutorial](http://pandas.pydata.org/pandas-docs/version/0.15.2/10min.html#min) 
and Geopandas documentation.

## What are Pandas or Geopandas -modules?

[**Pandas**](http://pandas.pydata.org) is a modern, powerful and feature rich library that is designed for doing data analysis in Python. 
It is a mature data analytics framework that is widely used among different fields 
of science, thus there exists a lot of good examples and documentation that can help you get going with your data analysis tasks. In Pandas the data is typically stored into a **DataFrame** 
that looks like a typical table with rows and columns (+ indices and column names), where columns can contain data of different data types. 
Thus, it reminds a little bit of how data is stored e.g. in Excel or in R that also uses a concept of dataframe.
 
Pandas takes advantage of **numpy** -module which runs under the hood, thus it is fast and powerful and can handle efficiently even large datasets. Pandas, however, makes some of the features in numpy 
much easier and more intuitive to use, such as creating new empty columns and doing data selections. Thus, it was useful to learn a little bit of how numpy works since many features included in pandas uses the same 
syntax as numpy. However, all numpy functions are not included in pandas, such as `np.linspace()` or `np.arange()`, hence it is really common to see that pandas and numpy -modules are both imported and used in a same Python script.
 
Compared to numpy, pandas is also a more flexible and feature rich module (or framework) as it combines functionalities from other scientific Python -modules as well, such as [**scipy**]() and [**matplotlib**]() 
for visualization purposes. Thus, you can use many of the features included in those packages even without importing them at all. 

[**Geopandas**]() is an extension built on top of Pandas module.

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


