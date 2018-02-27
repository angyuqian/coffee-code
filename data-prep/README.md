# Collect & Prep Your Data Workshop

This repository contains materials used in the Coffee & Code workshop: Collect & Prep Your Data for Visualization and Analysis.

## Handouts

- [Slides](/)
- [Sample Data](/)
- [Slightly Cleaned Sample Data](/)

## Exercise 1 (10 minutes)

- Do a [visual analysis of the Information Wanted dataset](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/UNJU3N)
- Consult the [Information Wanted Codebook](/)

## Exercise 2

Clean/Normalize
- Launch OpenRefine (a browser will open)
- Review basics
  - Undo/Redo tab
  - Common transforms
	- leading/trailing whitespace
	- change to upper/lowercase
	- data type
  - Export options
  - Split cells/columns
  - Text Facet & Clustering (useful for analysis)

### Tips & Recipes
- To trim all leading/trailing whitespace use:
  - value.trim()

- Remove all punctuation from text in a column:
  - Edit cells —> Transform —> value.replace(/\p{Punct}/,’’)

- Remove all punctuation at the end of a subject string:
  - Edit cells —> Split multi-valued cells —> Split by separator
  - Join multi-valued cells with a different separator
 
- Find and replace a specific character:
  - Edit cells —> Transform —> replace(value, “insert punctuation here“,””)

- Normalize dates (Transform function):
  - If you need to add leading zeros before day:
    value.toDate(‘dd’).toString(‘dd’)
  - If you need to add leading zeros before month:
    value.toDate(‘MM’).toString(‘MM’)
  - Modify format of year by adding “18” or “19” prefix:
    value.toDate(‘yyyy’).toString(‘18yy’) 
  - Convert abbreviations (month) to numeric date:
    value.toDate(‘MMM-yy’).toString(‘18yy-MM’)
  - Join the day, month, year into a single column:
    - Transpose cells across column into rows
    - Create one column: date
    - Join multi-valued cells and use a hyphen as separator
    - Move columns in order of year/month/date
      - can also flip: value.toDate(‘MM-dd-yyyy’).toString(‘yyyy-MM-dd’)

- Geocode location data
  - Add column by fetching URLs based on on column
  - Give your new column a name
  - Change throttle delay to 1000 milliseconds 
  - Use Expression:
    “http://nominatim.openstreetmap.org/search?format=json&email=[YOUR_EMAIL_HERE]&app=google-refine&q=" + escape(value, 'url')
  - Split your coordinates into two columns (latitude/longitude)
  - Use expression: value.parseJson()[0].lat
  - Repeat for longitude

- See [OpenRefine Recipes](https://github.com/OpenRefine/OpenRefine/wiki/Recipes) for additional tips


## Readings

- Schöch, [JDH: Big? Smart? Clean? Messy? Data in the Humanities](http://journalofdigitalhumanities.org/2-3/big-smart-clean-messy-data-in-the-humanities)
- Rawson and Muñoz, [Against Cleaning](http://curatingmenus.org/articles/against-cleaning)
- The Santa Barbara Statement on [Collections as Data](https://collectionsasdata.github.io/statement/)

## Resources
- [Getty Thesaurus of Geographic Names](http://www.getty.edu/research/tools/vocabularies/tgn/)
- [GPS Coordinates](https://www.gps-coordinates.net/)
- [OpenRefine](http://openrefine.org/)
- [TAPoR](http://tapor.ca/home) 
- [OpenRefine Documentation](https://github.com/OpenRefine/OpenRefine/wiki/Documentation-For-Users)
- [OpenRefine Date Functions](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Date-Functions )
- [Cleaning Data with OpenRefine, Programming Historian](http://programminghistorian.org/lessons/cleaning-data-with-openrefine)