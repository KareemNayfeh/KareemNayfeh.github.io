## Create remote points for specific named selections in ANSYS Mechanical with python scripting

Below is a simple code which takes already existing named selections and creates a corresponding remote point.

```python
namedSelections = DataModel.GetObjectsByName("Named Selections")[0].Children

final = []

for x in namedSelections:
    #filter which named selections you would like remote points for
    if x.Name.StartsWith("bearing"):
        final.append(x)

rp = Model.RemotePoints

for x in final:
    newRP = rp.AddRemotePoint()
    newRP.ScopingMethod= GeometryDefineByType.Component
    newRP.Name = x.Name + r"""_rp"""
    newRP.Location = x
    newRP.PilotNodeAPDLName = newRP.Name
```

```powershell
Write-Host "This is a powershell Code block";

# There are many other languages you can use, but the style has to be loaded first

ForEach ($thing in $things) {
    Write-Output "It highlights it using the GitHub style"
}
```
