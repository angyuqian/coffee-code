# Carto Workshop

## Handouts for workshop include:
1. GettingStartedCarto.pdf - outline with screenshots for getting started with CartoDB (using the sample data with coordinates)
2. CartoResources.pdf - links to tutorials and tips on additional functions in CartoDB, resources for cleaning, parsing, and geocoding data, as well as finding/creating/using historical maps for base layers
3. GeocodeTutorial.pdf - short tutorial on using Geocode add-on in Google Sheets to geocode your data

### For customization of data and visualization: 
* Sample SQL script to aggregate data and display it in the info pop-up box:

``` SQL
SELECT
the_geom_webmercator,
location_1,
venue,
image_url,
string_agg(dates::text,', ') event_dates,
count(1) cnt,
sqrt(count(1)) sqrtcnt,
max(cartodb_id) cartodb_id
FROM
sampleperfdata_europe
GROUP BY
the_geom_webmercator, location_1, venue, image_url
ORDER BY
cnt DESC
```

* CSS script to create markers sized by the square root of the number of venues in an area (or specify other element) and to add composite operations:
``` CSS 
#venues{
  marker-fill-opacity: 0.9;
  marker-line-color: #FFF;
  marker-line-width: 0;
  marker-line-opacity: 1;
  marker-placement: point;
  marker-type: ellipse;
  marker-width: 10*[sqrtcnt];
  marker-fill: #7B00B4;
  marker-comp-op: plus;
}
```
#### Add a historical map as the basemap in Carto
1. Example of geo-rectified <a href="http://mapwarper.net/maps/13354">historical map of Europe (1910)</a>
2. Go to Map View in Carto: select "add a custom basemap" and insert: http://mapwarper.net/maps/tile/13354/{z}/{x}/{y}.png for the XYZ URL

### Data set for this workshop
* SamplePerfData_Europe-no-coord.csv sample data set is taken from European performance data of Teresa Carreño during 1912 - 1916
* It includes the following data without coordinates : 

| Image URL | Dates | Year | Location 1 | Location 2 | Venue |

* SamplePerfData_Europe.csv sample data set is taken from European performance data of Teresa Carreño during 1912 - 1916
* It includes the following data with coordinates : 

| Image URL | Dates | Year | Location 1 | Location 2 | Venue | Latitude | Longitude |

* Dates are in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601</a> format 

### Sample data and maps in Carto

* <a href="https://akijas.carto.com/viz/add8d1d4-f1f9-11e5-9c19-0ea31932ec1d/public_map">European Performances 1912-1916 (non-aggregated)</a>
* <a href="https://akijas.carto.com/viz/080d8842-f6b0-11e5-a108-0e674067d321/public_map">European Performances 1912-1916 (aggregated with historical basemap)</a>

