# geo-bbox
This repo contains sample code that makes bounding boxes produced by neural network geo-aware. You can use this code to make polygons from your netwok's bboxes and then save them as vector files using [geopandas](https://geopandas.org/) or other libs.

### Usage
Example usage:
```python
from shapely.geometry import Polygon
from pyproj import Transformer


origin = [19.958494700836596, 50.046781124380225] # [0,0] point of the image -> top-left corner, can be lon/lat or easting/nortning - the order (x, y) is important
transformer = Transformer.from_crs("epsg:4326", "epsg:2180",always_xy=True) # transfrormer from lat/lon to EPSG:2180
bbox = [[98, 345], [420, 462]]  # top-left, bottom-right (in pixels)

result = geo_bbox(bbox=bbox, origin=origin, distance_per_pixel=0.1)
print(result)
```
The result:
`[[568614.4800091045, 242642.65476667695], [568646.6800091044, 242642.65476667695], [568646.6800091044, 242654.35476667696], [568614.4800091045, 242654.35476667696]]`