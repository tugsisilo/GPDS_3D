(tooltip)=
# Scripting Basics
It is finally time to put your Python skill to good use, but before you start coding, take some time to make preparations will make your life much easier.

## Scripting Workspace
Blender has pre-configured a **Scripting** workspace, switch to it and you will find some new areas along with old familiar faces.
```{figure} ../../assets/scripting/script_wp.png
:width: 100%
```
The **Python Console** area provides an interactive Python console with a history of your activities in the form of Python commands.
```{figure} ../../assets/scripting/py_console.png
```

The **Text Editor** area is where you can write your code in Blender, it has syntax highlight and some other basic tools.
```{tip}
:class: margin
No auto-completion at the time of writing (version 3.6.0).
```
```{figure} ../../assets/scripting/text_editor.png

```

The **Outliner** area is not new, but this time the `Display Mode` is set to `Blender file`, which lists all the data (including unused) currently in the file.
```{figure} ../../assets/scripting/outliner_bfile.png

```

## Turn on Python Tooltips
In `Edit > Preferences > Interface > Display`, tick `Developer Extras` and `Python Tooltips`. The tooltips give you the Python equivalent of the UI element, and you can copy it by <kbd>Right Mouse Click</kbd> the element and choose `Copy Python Command/Copy Full Data Path`.
```{figure} ../../assets/scripting/py_tooltip.png

```

## First Script
To make a new script, <kbd>Left Mouse Click</kbd> `New` on the header of the **Text Editor**. When writing Blender Python scripts, you always need to start with
````{tip}
:class: margin
You can also add the two convenience variables and convenience imports in the console to make things more consistant.
```python
from mathutils import *
from amth import *
C = bpy.context
D = bpy.data
```
````

```python
import bpy
```
and The `bpy` here is Blender in the form of a Python module. Now, let's find out how to add a cube using Python. Add one in the 3D viewport using the `Add` menu, and you will find this new entry in the history below the Python console.
```{figure} ../../assets/scripting/add_cube.png

```
Running this function in the console confirms that it does add a cube to the scene, and you can find out more about it in its [documentation](https://docs.blender.org/api/current/bpy.ops.mesh.html#bpy.ops.mesh.primitive_cube_add).
```{tip}
:class: margin
The **Python Console** area does have auto-completion, press <kbd>Tab</kbd> to use it.
```
```{figure} ../../assets/scripting/console_cube.png
---
name: console_cube
---
```
With this knowledge, we can write the following script to add cubes on the $y = z^2$ curve.
```python
import bpy

for i in range(10):
    bpy.ops.mesh.primitive_cube_add(size = 2, location = (0.0, i*i, i))
```
<kbd>Left Mouse Click</kbd> the {octicon}`triangle-right` on the header to run the script.
```{figure} ../../assets/scripting/first_cubes.gif
:width: 100%
```

## Using bpy module in Python
```{tip}
:class: margin
A script that works in Blender GUI may not work in command line.
```
If you want to render the scene on a remote machine, you can do it through the command line interface. Blender can be installed as a Python module, download the latest version from the [website](https://builder.blender.org/download/bpy/). Make sure you have a compatible version of Python (it is not always the latest version), then unzip and use `pip install` to install the module. Alternatively, you can [build it from the source](https://wiki.blender.org/wiki/Building_Blender/Other/BlenderAsPyModule).

`````{admonition} Use Visual Studio Code as Text Editor
:class: dropdown
If you are used to all the features and plugins **Visual Studio Code(VSCode)** has to offer, the text editor in Blender may feel quite lacking. Fortunately, there is a way to make VSCode and Blender work together. Search and install the extension called **Blender Development**, press <kbd>F1</kbd> or <kbd>Ctrl + Shift + P</kbd> to bring up `Command Palette`, then type `Blender: Start` and hit <kbd>Enter</kbd>(you may need administrator privileges). Choose the Blender executable and it will start a Blender instance linked to VSCode. You will know it is working if you see the `Dev` tab in the sidebar on the right side of the viewport.
```{figure} ../../assets/scripting/vscode_link.png
:width: 100%
```
Adding the following to your `settings.json` to save the trouble of finding the executable every single time:
```json
"blender.executables": [
{
    "path": "PATH_TO_BLENDER_EXECUTABLE",
    "name": "(optional)",
    "isDebug": false
}
],
```
To run a script, use `Blender: Run Script` in `Command Palette`.
```{figure} ../../assets/scripting/vscode_run_script.gif
:width: 100%
```
````{tip}
You are probably used to include something like this in your Python scripts:
```python
if __name__ == "__main__":
    main()
```
But at the time of writing(version 0.0.18) this will not work if you run the script using `Blender: Run Script`.
````
For auto-completion, you need to install a Python library called [**fake-bpy-module**](https://github.com/nutti/fake-bpy-module) following the instruction on its GitHub page.
`````

