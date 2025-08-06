[[Computer Graphics]]
Reduces the light to **Ambient, Diffuse and Specular**
The Illumination (color intensity) of a point is the sum of all those components.

### Ambient Light
Is used to simulate indirect lighting. Background light. Is independent of objects, viewer and light sources position. Can't have depth with just ambient light.

### Diffuse Light
Illumination that a surface receives from a light source. Is independent of viewer's position.
It depends on the light's position and the surface properties (normal, reflectance property).
Calculation is based on the Lambert's law.
As the angle between the light and the normal increases, the light's energy spreads across a larger area, is less intense. 

### Specular Light

Shininess reflected out of sources, the color depends on material. Specular light depend on both light source position and view position.


# Shading
Shading computes only lighting equations on the vertices, and interpolates the pixels in between.

**Flat/Constant Shading Model**
We define a normal at each polygon, not at each vertex. 
Evaluate the lighting equation at the center of each polygon using the associated normal. 
Each sample point on the polygon is given the interpolated lighting value at the vertices.

**Gouraud**
We define a normal vector at each vertex.
Evaluate the lighting equation at each vertex using the associated normal vector.
Each sample point color on the polygon is interpolated from the color values at the polygons vertices which were found in the lighting step.

**Phong**
Each vertex has an associated normal vector.
Evaluate the lighting equation at each vertex using the associated normal vector.
For every sample point on the polygon we interpolate the normal at the vertices of the polygon and compute the color using the lighting equation with the interpolated normal at each interior **pixel**.
