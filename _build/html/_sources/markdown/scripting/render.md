(render_scripting)=

# Rendering Using Python

camera set active



## Setup the Scene in Python

camera set active
```python
bpy.ops.object.camera_add(location=(0.0, 0.0, 2.75), rotation=(0.0, 0.0, 0.0))
C.scene.camera = C.active_object
```
CLI example



## Load .blend File
For complex setups, it might be easier to make it in Blender GUI and load the .blend file in Python script.
```python
bpy.ops.wm.open_mainfile(filepath=bl_path)
```




## Use bpy module in Python
If you want to render the scene on a remote machine, you can do it through the command line interface. Blender can be installed as a Python module, you can download the latest version from the [website](https://builder.blender.org/download/bpy/). Make sure you have a compatible version of Python (it is not always the latest version), then unzip and use `pip install` to install the module. Alternatively, you can [build it from source](https://wiki.blender.org/wiki/Building_Blender/Other/BlenderAsPyModule).