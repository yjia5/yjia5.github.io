## Add custom font to Anaconda envrionment

If the conda envrionment can not find specific font, when plotting the figures with matplotlib, for example
```
matplotlib.rcParams['font.family'] = 'Arial'
```
you may meet the problem like:
UserWarning: findfont: Font family ['Arial'] not found. Falling back to DejaVu Sans
(prop.get_family(), self.defaultFamily[fontext]))

To solve it, we need to download a font package and install it. Then we will get a font library containing $.ttf$ files.
Then there are two ways to fix the problem:
### 1. Copy this library (folder) directly to the envrionment folder
The envrionment folder for conda defaulty is at ".conda/envs/ENVRIONMENT_NAME". So only need to run
```
cp -r "FOND_LIBRARY_DIRECTORY" .conda/envs/ENVRIONMENT_NAME/font
```
This method is going to solve this problem anytime you run the python with this envrionment

### 2. Include the font library by python code

as:
```
import matplotlib.font_manager as font_manager

# Add every font at the specified location
font_dir = ["YOUR_FONT_DIRECTORY"]
for font in font_manager.findSystemFonts(font_dir):
    font_manager.fontManager.addfont(font)
```
