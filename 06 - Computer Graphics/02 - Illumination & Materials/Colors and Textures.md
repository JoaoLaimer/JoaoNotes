[[Computer Graphics]]
Each vertex can have a color, represented by a three dimension vector. The color in an object appear as a gradient between the color of each vector in a triangle.

Unless you're using a texture. Which has to map correctly to the shape of the object. To achieve this we use a UV map.

# UV Mapping
- u is the horizontal coordinate.
- v is the vertical coordinate.
The map is stored as a vertex information of the corresponding vertex.
A sampler outputs a color corresponding to the uv coords. 
The sampler is useful if the texture does not map well to the object, using different functions that can output different results.

# Filtering
Filtering is the process that actually assign the color to the uv coord using interpolation.
Linear interpolation creates a gradient between two coordinates.

# Mip Mapping
Is having a chain of lower resolution images of the  original texture 
