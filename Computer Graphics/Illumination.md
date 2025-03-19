The only way to see objects without light, is drawing just the color, but that way we lose depth.
With lighting we have depth.
 An "illumination model" describe inputs, assumptions, and outputs used to calculate illumination of surfaces.
 - Light Attributes (intensity, color, position, direction, shape).
 - Object Surface (color, reflectivity, transparency, etc.)
 - Interaction between lights and objects.

**Physicall y-Based** Illumination Models
Require accurate input data and few assumptions, rarely has enough information to specify all inputs, and takes a long time to compute.

**Non-Physically-based** Illumination Models
Focus on speed and efficiency, just need a good enough model for a specific application.

- Point Light: point to all positions
- Spot Light: cone light
- Directional Light: rectangle light

**Global Illumination**:  
The light comes from a source (direct illumination), sometimes light is blocked by another object, however, objects in the shadow can still receive light from it bouncing off other objects (indirect illumination).

**Local Illumination**:
Takes only direct lighting information, is a approximation of global illumination, usually involves the use of an "ambient" term to simulate indirect lighting.


