[[Computer Graphics]]
Rasterization is a "passive" renderer, vertices and geometric shapes are inputs and outputs the image.

Ray Tracing is an "active" renderer.

Ray Tracing maps rays from the camera (eye) through each pixel (Image Plane) to the objects in the scene. When a ray touches an object we map its color to the pixel.
If there is no intersection we render the background color.

There is three parts to a ray tracer:
- Generating rays: Shoot a ray from the eye through a sample point on the image plane that corresponds to a pixel.
- Ray-Object Intersection: For each object in the scene compute their intersection point.
- Calculate lighting: 
	- Local Illumination: Use illumination model to determine direct contribution from light sources.
	- Global Illumination: Recursively generate secondary rays that might contribute to the color of the pixel.

Ray Tracing iterates over PIXELS
Scan Conversion iterates over vertices.

**Generating a Ray**
- Ray Origin: Start from the camera position. P.
- Shoot ray from P towards any point on the film plane. **d** vector.

**Recursive Ray-Tracing**
Considers reflexes and refraction shooting new rays each time a reflexive material is found.


## Shadows
Umbra: no light (hard shadow)
penumbra: little light (soft shadow)
If a ray bounces (shadow ray) on a surface intersects an object and can't reach the light source.


### Tree of light rays
We can represent the recursive ray tracer using a tree.

### Ray Tracing Pipeline
Ray Generation -> Traversal and Intersection -> Shading.
