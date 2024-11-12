# lego_world_map
Code inspired from a project by [Milan Janosov](https://www.linkedin.com/in/milan-janosov/) to create a stylized elevation map of the world.

You can read about his work creating a Lego elevation map of Budapest [here](https://open.substack.com/pub/milanjanosov/p/lego-elevation-map?r=3mp6w8&utm_medium=ios) on his Substack.

## Downloading DEMs

I went to USGS' [EarthExplorer](https://earthexplorer.usgs.gov) to download all the GeoTIFF tiles from the Global 30 Arc-Second Elevation (GTOPO30) dataset:

![EarthExplorer webpage screenshot](figures/earth_explorer.png)

I manually downloaded all ~33 tiles in the dataset. Here's an example of what the raw GeoTiff looks like:

![GTopo30 Example: Caribbean](figures/gt30w100n40_down.jpg)

## Merging DEMs

The challenge here was finding the right process to merge the DEMs, as each one was on the order of 50 MB. What worked was to [create a VRT](https://gdal.org/en/latest/programs/gdalbuildvrt.html), or Virtual Raster Table, which helps relieve the memory burden for the system.

Using matplotlib, it was easy to save the resulting .tif file as a JPG for pretty viewing:

![JPG of merged worldwide DEM](figures/dem_world.jpg)

