# lego_world_map
Code inspired from a project by [Milan Janosov](https://www.linkedin.com/in/milan-janosov/) to create a stylized elevation map of the world.

You can read about his work creating a Lego elevation map of Budapest [here](https://open.substack.com/pub/milanjanosov/p/lego-elevation-map?r=3mp6w8&utm_medium=ios) on his Substack.

Lego has previously made a world map (see below), but I think I could do a little better!

![Lego's world map](figures/LEGO-31203-World-Map-Product-Photo-1024x815.jpg)

## Overview<a name='over'></a>


## Table of Contents<a name='toc'></a>

[Downloading DEMs](#dem)
[Merging DEMs](#merge)
[Create Grid](#grid)

## Downloading DEMs<a name='dem'></a>

I went to USGS' [EarthExplorer](https://earthexplorer.usgs.gov) to download all the GeoTIFF tiles from the [Global 30 Arc-Second Elevation (GTOPO30)](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-digital-elevation-global-30-arc-second-elevation-gtopo30?qt-science_center_objects=0#qt-science_center_objects) dataset:

![EarthExplorer webpage screenshot](figures/earth_explorer.png)

I manually downloaded all 33 tiles in the dataset. Here's an example of what the raw GeoTiff looks like:

![GTopo30 Example: Caribbean](figures/gt30w100n40_down.jpg)

## Merging DEMs<a name='merge'></a>

The challenge here was finding the right process to merge the DEMs, as each one was on the order of 50 MB. What worked was to [create a VRT](https://gdal.org/en/latest/programs/gdalbuildvrt.html), or Virtual Raster Table from the GDAL library, which helps relieve the memory burden for the system.

Using matplotlib, it was easy to save the resulting .tif file as a JPG for pretty viewing:

![JPG of merged worldwide DEM](figures/dem_world.jpg)

## Create Grid<a name='grid'></a>

Now we have to rasterize the elevation map. This is crucial as we'll be eventually making this map in Lego, which are bricks (duh).

We need to have a look at the boundaries of the world. I have a file downloaded already. Since the file has an entry for every country, we will get distracting boundary lines in our polygon. Using the `union_all` method, I can merge all the polygons into a single massive polygon. Let's take a look at the result:

![World polygon](figures/world_polygon.jpg)

We'll have to figure out what the dimensions of the Lego set are (in Lego studs), as that is a good reference size for our eventual Lego map.
* The map is 5 x 16 or 80 studs in height and
* 8 x 16 or 128 studs in width

Using a function from Milan, we can create a grid over the polygon. Let's look at the contiguous USA:

![Grid on polygon of the contiguous USA](figures/grid_usa.jpg)
