## Exporting Solutions in Ansys as Videos


Below is a simple ansys script written in python to export solutions as MP4 videos

```python
image_settings = Ansys.Mechanical.Graphics.GraphicsImageExportSettings()
image_settings.CurrentGraphicsDisplay = True

fileLoc = r"""C:\Users\karee\ANSYS\videoDemo.""" 
# videoDemo. is the prefix that all exported mp4's would have

# Getting an array of all solved solutions
solutions = DataModel.GetObjectsByName("Solution")[0].Children

# Video settings
Graphics.ResultAnimationOptions.NumberOfFrames = 8
Graphics.ResultAnimationOptions.Duration = Quantity(3,'s')

# Looping through every solution excluding index 0 (solution information) and exporting it
for x in list(solutions)[1:]:
    x.RenameBasedOnDefinition()
    x.ExportAnimation(fileLoc + x.Name.Replace(" ", "") + """.mp4""", GraphicsAnimationExportFormat.MP4)
    Graphics.ExportImage(fileLoc + x.Name.Replace(" ", "") + "IMG", GraphicsImageExportFormat.PNG, image_settings)

```
