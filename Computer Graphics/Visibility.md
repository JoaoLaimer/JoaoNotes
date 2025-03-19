Object Space: The scene with the objects.
Culling: Choosing what to render.

# Frustum Culling: 
## Brute Force
Comparing the normals of the frustum with the normals of the vertex of the objects, using dot product.

## Bounding Box
If an object has a lot of vertices, we can put it in a box that just fits the object and compare the vertices of the box.
Doesn't need to be necessarily a box, it can be a sphere, cylinder or a custom polygon.
We also can use more than one bounding box in one object, improving the hierarchy.

## Spatial Subdivision
We can split the space, using a tree like structure called quadtree. Each level of the tree splits the space even more, if the object is in the same division of the camera it is drawn.
We use Quadtrees for culling, collision and data compression.

## Octree
Quadtrees only deal in a bi-dimensional way, this can cause objects that are out of view in the y-axis to be drawn unnecessarily.
Octree fixes this issue, subdividing the space in a three-dimensional way.