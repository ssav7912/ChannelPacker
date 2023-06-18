# ChannelPacker
 
 Quick and Dirty channel packing utility I wrote because it's needlessly difficult to do with ImageMagick and every other tool I looked at was GUI based (or required you to open Photoshop...). 
 This was used to help make my life easier swizzling packed data maps for a game engine that used an unorthodox method of packing, so the defaults are a bit silly.
 
 Requires Python 3 and Pillow (PIL). Tested on Python 3.8 and PIL 8.1.
 
 ### Usage
Invoke from the command line: 

 `python pack.py [-h] [-r r.png or 0-255] [-g g.png or 0-255] [-b b.png or 0-255] [-a a.png or 0-255] output`
 
Either a path to an image (of any format PIL supports) or an integer in the range 0-255 may be provided to each switch. If a switch is omitted, it will use the default described below.
Appending a ':' followed by any of 'R,G,B,A' to a path string will pull that channel out of the specified image. 
If all switches are integers it will produce an 8x8 output image. 

 ```
positional arguments:
  output                The output filename

optional arguments:
  -h, --help            show this help message and exit
  -r r.png or 0-255, --red r.png or 0-255
                        Red Channel Input. Default value is 0
  -g g.png or 0-255, --green g.png or 0-255
                        Green Channel Input. Default value is 255
  -b b.png or 0-255, --blue b.png or 0-255
                        Blue Channel Input. Default value is 255
  -a a.png or 0-255, --alpha a.png or 0-255
                        Alpha Channel Input. Default value is 0
```

### Examples
Swizzle RGB to BGR:

`python pack.py -r RGB.png:B -g RGB.png:G -b RGB.png:R -a 255 BGR.png`

Create AORM from separate maps:

`python pack.py -r ao.png -g roughness.png -b metallic.png -a 255 AORM.png`

Create an AORM map for a dielectric PBR material that only specifies a roughness map:

`python pack.py -r 255 -g roughness.png -b 0 -a 255 AORM.png`


 ### Installation
 Requires PIL. Install PIL with `pip install pillow`.
 
 Copy the script to desired directory. Run with `python pack.py`. Profit.
