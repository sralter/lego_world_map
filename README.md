# lego_world_map
Code inspired from Milan Janosov to create a stylized elevation map of the world.

You can read about his work creating a lego elevation map of Budapest [here](https://open.substack.com/pub/milanjanosov/p/lego-elevation-map?r=3mp6w8&utm_medium=ios) on his Substack.

The key code was borrowed from [this](https://gis.stackexchange.com/questions/449569/merging-a-large-number-of-geotiff-files-via-gdal-merge-py) substack post.

## Downloading DEMs

I went to USGS' [EarthExplorer](https://earthexplorer.usgs.gov) to download all the tiles from the Global 30 Arc-Second Elevation (GTOPO30) dataset:

![EarthExplorer webpage screenshot](figures/earth_explorer.png)



Using matplotlib, it was easy to save the resulting .tif file as a JPG for pretty viewing:

![JPG of merged worldwide DEM](figures/dem_world.jpg)
