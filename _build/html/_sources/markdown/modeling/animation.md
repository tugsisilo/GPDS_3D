(animation)=
# Animation
In 3D modeling, animation means moving objects and/or making them change shape over time. Just like the previous topics, we will focus on the basic concepts.

## Frame
You may already know that videos are made of 24 or more images per second, and these images are called **Frames**. The concept of frames in 3D animation is mostly the same. On the `Output` tab in the properties area, you can change the frame rate (frame per second) of the current scene in `Format > Frame Rate`, and its range in `Frame Range`.

```{figure} ../../assets/modeling/frame.png
```
## Keyframe
**Keyframes** store the values of properties at a certain frame. To add a keyframe, first move the current frame to the one you want to add the keyframe in the **Timeline** area (or change `Current Frame` on the header), then select the object and press <kbd>I</kbd> while the cursor is hovering on the property, or just press <kbd>I</kbd> to bring up the `Insert Keyframe Menu` and select the desired option. When you want to delete it, press <kbd>Alt + I</kbd> instead. A property with a <span style="background-color:yellow">yellow</span> background means it is keyframed on the current frame; a <span style="background-color:green">green</span> background means it is keyframed on another frame; an <span style="background-color:orange">orange</span> background means the value is changed from the keyframed one. After adding the keyframes, press <kbd>Spacebar</kbd> or <kbd>Left Mouse Click</kbd> the play icon to play the animation.
```{tip}
:class: margin
This works on all kinds of objects, including [cameras](Camera) and [lights](Lighting).
```
```{figure} ../../assets/modeling/keyframe.gif
:width: 100%
```

## Driver
**Drivers** allow you to use a function as an input value, and a property with a driver is displayed with a <span style="background-color:purple">purple</span> background. Press <kbd>Ctrl + D</kbd> or <kbd>Right Mouse Click</kbd> and choose `Add Driver` on a property to add a driver to that property. You can edit the `Expression` and choose/add variables in the `Driven Property` menu. To access the menu again, <kbd>Right Mouse Click</kbd> on the property and choose `Edit Driver`.  If a driver is not working as intended, you can try the `Update Dependencies` option in the menu.
```{tip}
:class: margin
It might be hard to figure out where the variable locates in the data when you are new to this. A easy way of making variables is <kbd>Right Mouse Click</kbd> on a property, choose `Copy as New Driver`, then <kbd>Left Mouse Click</kbd> the `Paste Driver Variables` icon on the right side of the `Add Input Variable` button.
```
```{figure} ../../assets/modeling/driver.gif

```
A useful shortcut is `#frame`, putting it in as a value automatically creates a `Driver` that outputs a value equal to the number of the current frame. You can also add some simple math in there, for example, if the frame number is too big for the variable, you can do something like `#frame/1000`.
```{tip}
:class: margin
If there is already a driver on that property, you need to delete it first for `#frame` to work.
```
```{figure} ../../assets/modeling/driver_shortcut.gif
:width: 100%
```


## F-Curve
You may have noticed that in the animation examples above, the cube does not move at a constant speed. The keyframes determine the state of the object at certain frames, but how the in-between frames should be interpolated need to be decided in other ways. Change one of the areas in your workspace to `Graph Editor` and select an animated object, then the **F-Curve** will show up. Edit it will change how the interpolation works for the animation of the object per animated property.
```{tip} 
:class: margin
Editing the F-curve is similar to editing a Bezier curve but in 2D.
```
```{figure} ../../assets/modeling/f_curve.gif
:width: 100%
```