# Hints for Exercise 2

## Reading data to Pandas

Pandas can read data from many different sources such as text or csv files, excel files, or from different databases. 
Let's consider reading a hypothetical file called myFile.txt that has following content:

 ```
 value;lat;lon
 0;2;4
 5;1;6
 2;6;1
 6;6;3
 5;5;1
 ```


Reading data from text or csv file can be done easily by using 
[ `.read_csv()` ](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html) - function. Notice that the separator in the file is `;` -character.  

 ```python
 # Determine filepath
 fp = r"/home/geo/myFile.txt"
 
 # Read data
 data = pd.read_csv(fp, sep=';')
 
 >>> print(data)
    value  lat   lon
 0    0     2     4
 1    5     1     6
 2    2     6     1
 3    6     6     3
 4    5     5     1
 ```
  
## Converting Pandas DataFrame into a GeoDataFrame

Quite often you are in a situation where you have read data e.g. from text file into a Pandas DataFrame where you have latitude and longitude columns representing the location of a record. 

- Let's continue with the previous example and consider that we have a column where we have stored the shapely geometries:

 ```python
 >>> print(data)
     value  lat  lon     geometry
 0      0    2    4  POINT (4 2)
 1      5    1    6  POINT (6 1)
 2      2    6    1  POINT (1 6)
 3      6    6    3  POINT (3 6)
 4      5    5    1  POINT (1 5)
 ```
 
 - Notice that now our data is still a Pandas **DataFrame**, not a GeoDataFrame:
 
 ```python
 >>> type(data)
 pandas.core.frame.DataFrame
 ```

- We need to convert the DataFrame into a GeoDataFrame, so that we can e.g. save it into a Shapefile. It is easily done by passing the DataFrame into a GeoDataFrame object. We need to determine 
 which column contains the geometry information (needs to be always a column called 'geometry'), and optionally we can also determine the coordinate reference system when creating the GeoDataFrame:
 
 ```python
 # Convert DataFrame into a GeoDataFrame
 geo = gpd.GeoDataFrame(data, geometry='geometry', crs=from_epsg(4326))

 >>> type(geo)
 geopandas.geodataframe.GeoDataFrame
 
 >>> geo.crs
 {'init': 'epsg:4326', 'no_defs': True}
 ```
 Now we have converted Pandas DataFrame into a proper GeoDataFrame that we can export into a Shapefile for instance.  