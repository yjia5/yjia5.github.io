## Add custom font to Anaconda envrionment

If the conda envrionment can not find specific font, when plotting the figures with matplotlib, for example
```
matplotlib.rcParams['font.family'] = 'Arial'
```
you may meet the problem like:
```
UserWarning: findfont: Font family ['Arial'] not found. Falling back to DejaVu Sans
(prop.get_family(), self.defaultFamily[fontext]))
```

To solve it, we need to download a font package and install/unzip it. Then we will get a font library `YOUR_FONT_LIBRARY` containing `.ttf` files.
It is supposed to solve the problme by including the font library by python code as:
```
import matplotlib.font_manager as font_manager

# Add every font at the specified location
font_dir = ["YOUR_FONT_DIRECTORY"]
for font in font_manager.findSystemFonts(font_dir):
    font_manager.fontManager.addfont(font)
```

However, on HCC, it may not able to work. If so, you can manually copy the fonts (`.ttf` files) into the default search directory. To find the search directory, you can use
```
font_manager.findfont("DejaVu")
```
which show the path of font `DejaVu`: `DEFAULT_PATH`. Then you can copy the fonts you want into this path.

```
cp YOUR_FONT_LIBRARY/* DEFAULT_PATH
```
