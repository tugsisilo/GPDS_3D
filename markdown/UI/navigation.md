(navigation)=
# Navigation

Navigating the 3D space on a 2D screen may take a bit of getting used to, but if you've played any city-builders or tycoon games, now you can tell your mom what a great learning experience that has been. In this section, we will focus on the **3D Viewport** area, make sure you have one on your screen if you changed the default layout in the last section.

## 3D Viewport

The **3D Viewport** is the area you will be staring at most of the time until you start to learn scripting. It is where you interact with everything in your 3D scene. You may want to call it a camera, but in Blender, the **Camera** represents the point of view for rendering, which we will explain in a later chapter.

```{figure} ../../assets/UI/3D_viewport.PNG
:width: 100%
```

## Orbiting and Panning

To **Orbit** a point in the 3D space, hold <kbd>Middle Mouse Button</kbd> and move your mouse. Alternatively, you can use this gizmo in the top right corner by holding <kbd>Left Mouse Button</kbd>.

```{tip}
:class: margin
By default the point will be the `World Origin`, where the coordinate is (0, 0, 0).
```

```{figure} ../../assets/UI/gizmo_1.png

```

To change the object you are currently orbiting, <kbd>Left Mouse Click</kbd> to select an object, then press <kbd>Numpad .</kbd> or use the menu `View > Frame Selected`.

```{tip}
:class: margin
- Memorizing some common keyboard shortcuts/hotkeys is essential if you want to become proficient. If you want to assign/change a short cut, <kbd>Right Mouse Click</kbd> on the operation to bring up the option. Alternatively, you can add it to `Quick Favorites`, which is a menu you can access by pressing <kbd>Q</kbd>
- This tutorial use the add-on [**Screencast Key**](https://github.com/nutti/Screencast-Keys) to visulize keyboard and mouse inputs.Please ignore **F7** since it's the hotkey for screen recording.
```

If you want to move the viewport while keeping the direction you are looking at, hold <kbd>Shift + Middle Mouse Button</kbd>, and this operation is called **Panning**. Beware that panning moves the center point that you are currently orbiting.

```{figure} ../../assets/UI/viewport_orbit_pan.gif
:width: 100%
```

## Zooming

<kbd>Scroll</kbd> to `Zoom` in and out, or hold Ctrl</kbd> and <kbd>Middle Mouse Button</kbd> to have finer control.

```{figure} ../../assets/UI/zoom.gif
:width: 100%
```

Sometimes you may encounter the problem that you want to zoom in but Blender just refuses to do so. Usually, the reason is you are getting too close to the point that you are orbiting. In that case, you can set the point to an object by selecting it and pressing <kbd>Numpad .</kbd> as mentioned in the last section.

When the viewport gets too close to a 3D object, you may see through the surface of it, and this is called **Clipping**. You can change the value of `Clip Start` to modify this behavior.

```{figure} ../../assets/UI/zoom_clip.PNG

```

## Orthographic Views

The front, side, and top **Orthographic Views** are very helpful when modeling with reference pictures. <kbd>Numpad 1</kbd>, <kbd>Numpad 3</kbd>, <kbd>Numpad 7</kbd> gives you quick access to them. If you are using a laptop with no numpad, you can use the aforementioned gizmo by <kbd>Left Mouse Click</kbd> on the little balls with X, Y and Z on them.

## Fly/Walk Navigation

If you love first-person games, this one will make you feel right at home. You can find them in `View > Area > Navigation`, look around using your mouse and move with <kbd>W</kbd><kbd>A</kbd><kbd>S</kbd><kbd>D</kbd> or <kbd>↑</kbd><kbd>↓</kbd><kbd>→</kbd><kbd>←</kbd>. Once you are finished, exit by pressing <kbd>Esc</kbd>. They are probably not very useful for the purpose of this tutorial, but it is nice being able to fly/walk through the 3D scene you made.
