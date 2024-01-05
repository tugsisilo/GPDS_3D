(Lighting)=
# Lighting
Without light, you are not able to see anything, and so is the camera. **Lighting** can drastically change the look of a 3D scene, just like in real life.

## Types of Light

::::{tab-set}
:::{tab-item} Point Light
A **Point Light** is a light source that emits light in all directions like a light bulb. You can adjust its brightness by changing `Light > Power` and its size in `Light > Radius`.
```{tip} 
:class: margin
The radius of the light will effect how shadows look, smaller values will produce more defined edge, larger ones will give you soft shadows.
```
```{figure} ../../assets/render/point_light.png
:width: 100%
```
:::

:::{tab-item} Sun Light
The **Sun Light** provides directional light with constant brightness from far away. The location of the light object has no effect, but the direction can be adjusted by rotating the object or dragging the yellow circle. Keep in mind that the brightness of `Sun Light` is measured differently compared to other light types.
```{figure} ../../assets/render/sun_light.png
:width: 100%
```

:::

:::{tab-item} Spot Light
A **Spot Light** emits a cone-shaped light, like the ones on stages. Dragging the blue arrow adjusts the angle of the cone.
```{figure} ../../assets/render/spot_light.png
:width: 100%
```

:::


:::{tab-item} Area Light
An **Area Light** simulates light emitted from a surface, like the lights used in studios. You can change its facing by dragging the yellow circle, and its shape in `Light > Shape`.
```{figure} ../../assets/render/area_light.png
:width: 100%
```
:::

:::{tab-item} IES 
**IES(Illuminating Engineering Society)** files contain directional light intensity distribution data, and it can be used to recreate real-world lights. To use it, Add a **Point Light**, and <kbd>Left Mouse Click</kbd> `Nodes > Use Nodes`. Then in the shader editor, add an **IES Texture** node, open the IES file and connect the `Fac` output to the `Strength` socket of the `Emission` node.
```{tip} 
:class: margin
The IES file in this example is obtained from [ies library](https://ieslibrary.com/en/home).
```
```{figure} ../../assets/render/ies_light.png
:width: 100%
```
:::

::::


## Three-point Lighting
A standard way of setting up lighting is called **Three-point Lighting**, and it consists of three different lights as its name suggests. The first one is called **Key Light**, it is the main light source that defines the overall setup.
```{figure} ../../assets/render/key_light.png
:width: 100%
```
The second light is the **Fill Light**, it is weaker than the key light and positioned on the opposite side to soften the contrast.
```{figure} ../../assets/render/fill_light.png
:width: 100%
```
The last one is the **Backlight**, which separates the object from the background.
```{figure} ../../assets/render/backlight.png
:width: 100%
```
The **Tri-lighting** add-on can automatically set this up for you. Enable it in `Edit > Preferences... > Add-ons`, then select an object and choose `Light > 3 Point Lights` in the `Add` menu. This creates 3 area lights and a camera pointing at the object, you can tweak them to your liking.
```{figure} ../../assets/render/tri_lighting.gif
:width: 100%
```

## HDRI
If you want to know how your 3D object would look in a real-life place, **HDRI(High Dynamic Range Image)** can help you. HDRIs are 360° images that include lighting information. To add an HDRI to your scene, switch the tab in the properties area to `World`, then <kbd>Left Mouse Click</kbd> on the yellow dot on the right of `Surface > Color` and choose `Environment Texture`. <kbd>Left Mouse Click</kbd> `Open` to load the HDRI.
```{tip} 
:class: margin
- The yellow dot is an input socket of the **Background** node, you actually added a `Environment Texture` node and connected to the input by choosing the option. In the shader editor, you can check the node tree for the `World` by switch `Shader Type` on the top left.
- The HDRI file in this example is obtained from [Poly Haven](https://polyhaven.com/hdris).
```
```{figure} ../../assets/render/hdri.png
:width: 100%
```
An alternative is to use the **Sky Texture**. It simulates sunlight and you can tweak the position of the sun and atmospheric conditions.
```{figure} ../../assets/render/sky_tex.png
:width: 100%
```

