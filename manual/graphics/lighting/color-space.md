# Color Space

![Properties](../post-effects/media/color-grading-wheel.png)

[Graphics Settings](../../editor/game-settings/graphics-settings.md) have an option `Gamma Color Space` that controls the logic of importing sRGB color textures. If checked, color space workflow will use Gamma instead of Linear. Gamma color space defines colors with an applied a gamma curve (sRGB) so they are perceptually linear. This makes sense when the output of the rendering represent final color values that will be presented to a non-HDR screen. When unchecked, color textures imported as sRGB will be properly lit to output exact colors as input textures. This option affects the final image presentation to the window backbuffer, meaning all lighting operations are correctly performed in linear color space.

### Linear Color Space

When using preferred linear lighting workflow, the colors pipeline follows:
* textures imported with `sRGB` option are encoded into `sRGB` format,
  * default for diffuse/albedo textures,
  * data is sRGB but GPU transforms it back to linear when sampling in a shader,
* all other textures are imported as linear,
* material shaders read texture data and input colors as linear,
* lighting performs shading and blending in linear color space (HDR),
* various visual effects are in linear color space (DoF, Fog, Eye Adaptation, Bloom),
* Color Grading transforms colors with:
  * White Balance,
  * Color Correction,
  * Tonemapping (ACES, AgX),
  * LDR LUT,
* colors are transformed to display color space (sRGB),
* final post-processing happens (Film Grain, Vignette).
