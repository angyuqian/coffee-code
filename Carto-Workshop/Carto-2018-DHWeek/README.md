# Introduction to Spatial Visualization & Analysis with Carto
This [workshop](http://libcal.bc.edu/event/3914095?hs=a) is offered as part of [Boston DH Week 2018](https://docs.google.com/spreadsheets/d/16LmLmmIEFCcamh7dwVX6N2FZ199VLPnt8VWMbKI1u_I/edit) and is co-taught by [Anna Kijas](https://ds.bc.edu/people/) (Boston College) and [Ece Turnator](https://libguides.mit.edu/directory/lirs#s-lg-box-wrapper-14366446) (MIT).

## Learning Goals
This workshop will introduce participants to visualizing spatial data, creating maps with points and polygons, and performing basic data analysis with [Carto](https://carto.com/). Participants will get a hands-on experience using the Carto platform and will learn how to geocode point data in [OpenRefine](http://openrefine.org/) using [GREL string functions]( https://github.com/OpenRefine/OpenRefine/wiki/GREL-String-Functions), and review examples and resources for georeferencing maps and adding basemaps.

## Workshop Overview
1. Why do we want to visualize spatial data?
    - GIS terms

2. Intro to the dataset - [Cambridge, MA Crash Data](/Carto-Workshop/Carto-2018-DHWeek/carto_sample_data.zip) 

3. Geocoding Location Data with OpenRefine
    - Launch OpenRefine from your applications and a browser will open
    - Download and unzip [datasets](insert link) to your machine
    - Upload sample-info-wanted-dataset.csv to OpenRefine
      - Add column by fetching URLs based on on column
      - Give your new column a name
      - Change throttle delay to 1000 milliseconds 
      - Use Expression: 
`"http://nominatim.openstreetmap.org/search?format=json&email=[YOUR_EMAIL_HERE]&app=google-refine&q=" + escape(value, 'url')`
    - Split your coordinates into two columns (latitude/longitude)
      - Use expression: `value.parseJson()[0].lat`
      - Repeat for longitude (.lon)

4. Intro to the Carto dashboard and platform
   - Points layer
   - Polygon layer
   - Widgets and analysis tools
   - Export and share data
   - Publish and embed data
   - Custom CSS and SQL
  
5. How to add your own basemap
   - Where to find georeferenced maps
   - Using georeferencing tools
   - Maps that have been georeferenced can be pulled in to software, such as Carto, by providing the URL from the basemap provider, such as a Web Mapping Service (WMS) or Web Mapping Tile Service (WMTS). The list below includes ready-to use basemaps as well as georeferencing tools.  
   
     - [David Rumsey Map Collection & Georeferencer](https://www.davidrumsey.com/view/georeferencer)
     - [Map Warper](http://mapwarper.net/)
     - [MapTiler](https://www.maptiler.com/how-to/georeferencing/)
     - [NYPL Map Warper](http://maps.nypl.org/warper/)
     - [Spatineo Directory](http://directory.spatineo.com/)
     - [USGS Historical Topographic Map Collection](https://catalog.data.gov/dataset/usgs-historical-topographic-map-collection)


## General Map and GIS Data Resources
- [GIS Libguide (MIT)](https://libguides.mit.edu/gis/)
- [Finding Spatial Data for Mapping (BC)](https://libguides.bc.edu/gis)
- [MIT maps guide](https://libguides.mit.edu/maps)
- [MIT GeoWeb](https://arrowsmith.mit.edu) 
- [British Library Maps](https://www.bl.uk/subjects/maps) 
- [David Rumsey map collection](https://www.davidrumsey.com/)
- [Europeana map colection](https://www.europeana.eu/portal/en/collections/maps)
- [DPLA](https://dp.la/) (refine your search by Subject Search >  Maps)
- [Ancient Places via Pleiades (downloads available)](https://pleiades.stoa.org/downloads)
- [Social Explorer](http://www.socialexplorer.com/)
- [Hathi Trust](https://babel.hathitrust.org/cgi/ls?a=page;page=advanced) (Advanced search> Format: “Map”) 
- [Classical Atlas Project (University of North Carolina)](http://awmc.unc.edu/wordpress/free-maps/)
- [Digital Atlas of Roman and Medieval Civilizations (Harvard University)](https://darmc.harvard.edu/)
- [Digital Map Collection (University of California, Berkeley)](http://www.lib.berkeley.edu/EART/browse.html)
- [Discovery and Exploration (Library of Congress)](http://lcweb2.loc.gov/ammem/gmdhtml/dsxphome.html)
- [Map History/History of Cartography (Website maintained by former map librarian at the British Library)](http://www.maphistory.info/)
- [Old Maps Online (University of Portsmouth)](http://www.oldmapsonline.org/#bbox=-71.562195,42.159332,-70.562439,42.55915&q=&datefrom=1000&dateto=2010)
- [Perry-Castaneda Library Map Collection (University of Texas-Austin)](http://www.lib.utexas.edu/maps/historical/index.html)
- [UPenn Historical Maps LibGuide](https://guides.library.upenn.edu/historical_maps/mapoverlays)


