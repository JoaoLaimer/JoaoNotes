[[Computer Graphics]]
# Back Face Culling
How can you not render the back face of an object?
Calculating the dot product normals between the camera and the object face, if the product is lower than 0, it means that the face of the object is facing the camera and the object has to be drawn, if the product is higher than 0, we don't draw the face.

A better approach is checking in which direction the triangle has been draw, the vertices are drawn counter-clock-wise it means the it's a front-facing triangle, if clock-wise it is back-facing.

# Scene Depth
Z defines the depth of the vertex.

**Painter Algorithm**: We sort all **objects** in a scene by distance on the projection plane and 
draw the closest **object** first. Can cause some objects to be incorrectly drawn.

**Z-buffer / Depth Buffer**: Creates a buffer by depth, and draw only the closest z coord in the pixel.

We use the Painter Algorithm in combination with the z-buffer, we use the painter first than the z-buffer as to not draw a object twice.

**Depth Fighting or Z-Fighting**: When two objects are coplanar. Occupy the same space. What is draw depends on the precision of the float used.


