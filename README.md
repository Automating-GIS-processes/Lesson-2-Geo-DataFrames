# Lesson 2: Working with Geo-DataFrames in Pandas and Geopandas

**NEW!**: You can optionally read these materials from a new website. Go to [https://automating-gis-processes.github.io/2016/](https://automating-gis-processes.github.io/2016/).

At this point, we have learned few things about how to deal with data and do processes using Python's own 
functionalities or using [numpy -module](http://www.numpy.org/). This week we will start using a specific Data Analysis Library in Python called [**Pandas**](http://pandas.pydata.org/) and its 
spatial extension [**Geopandas**](http://geopandas.org/) that make working with data and geospatial data easy, efficient and fast. 
  
## Lesson overview:

 1. [Introduction to Pandas and Geopandas](Lesson/pandas-geopandas.md) 
   - [What are Pandas or Geopandas -modules](Lesson/pandas-geopandas.md#what-are-pandas-and-geopandas--modules)
   - [Data in / out](Lesson/pandas-geopandas.md#data-io-in--out) 
   - [Coordinate reference system (CRS)](Lesson/pandas-geopandas.md#coordinate-reference-system-crs)
   - [Geometries in Geopandas](Lesson/pandas-geopandas.md#geometries-in-geopandas)
   - [Grouping data](Lesson/pandas-geopandas.md#grouping-data)
 2. [Exercise 2](https://classroom.github.com/assignment-invitations/f6f1d09cc0e970fcec4f3556b6754f4d)

## Resources

- Past lesson materials
  - [Introduction to Python-GIS](https://github.com/Automating-GIS-processes/Lesson-1-Intro-Python-GIS)
  - [Plotting in Python](https://github.com/Python-for-geo-people/Lesson-7-Plotting)
  - [Intro to Numpy](https://github.com/Python-for-geo-people/Lesson-6-Intro-to-NumPy)
  - [Reading and Writing files](https://github.com/Python-for-geo-people/Lesson-5-Reading-Writing)
  - [Functions and modules](https://github.com/Python-for-geo-people/Functions-and-modules)
  - [Control flow](https://github.com/Python-for-geo-people/Control-flow)
  - [Intro to version control and GitHub](https://github.com/Python-for-geo-people/Diving-into-Python/tree/master/Lesson/intro-to-GitHub.md)
  - [Writing script files](https://github.com/Python-for-geo-people/Diving-into-Python/tree/master/Lesson/writing-scripts.md)
  - [Working on the exercises](https://github.com/Python-for-geo-people/Diving-into-Python/tree/master/Lesson/working-on-assignment.md)
- Web pages
  - [Shapely documentation](http://toblerity.org/shapely/manual.html)
  - [Codecademy's Learn to program in Python](https://www.codecademy.com/learn/python)
  - [Software Carpentry's programming in Python](https://swcarpentry.github.io/python-novice-inflammation/)
- Books
  - [Learning Geospatial Analysis with Python: An effective guide to geographic information systems and remote sensing analysis using Python 3](https://www.packtpub.com/application-development/learning-geospatial-analysis-python-second-edition)
  - [Python for Data Analysis: Data wrangling with Pandas, NumPy and iPython](http://www.amazon.com/Python-Data-Analysis-Wrangling-IPython/dp/1449319793)
  - [Python Geospatial Development: Develop sophisticated mapping applications from scratch using Python 3 tools for geospatial development](https://www.packtpub.com/application-development/python-geospatial-development-third-edition)
  - [Python Scripting for ArcGIS](https://www.amazon.com/Python-Scripting-ArcGIS-Paul-Zandbergen/dp/1589482824/ref=asap_bc?ie=UTF8)
  - [Python Geospatial Analysis Cookbook: Over 60 recipes to work with topology, overlays, indoor routing, and web application analysis with Python](https://www.packtpub.com/big-data-and-business-intelligence/python-geospatial-analysis-cookbook)
  - [Learn Python the Hard Way](http://learnpythonthehardway.org/book/)
  - [Dive into Python 3](http://www.diveinto.org/python3/)
