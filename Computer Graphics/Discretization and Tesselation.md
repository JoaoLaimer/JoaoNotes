# Rendering
Process of computing a image, often it uses a GPU for it.
Highly parallel process.

# Point Cloud 
A process of discretization of an object, the more LOD (level of detail) more points.

# Function Discretization
Using existing functions you can sample each point on top of a curve of a function to describe shapes.
You can use the exponential curve, Cubic Bézier Curve, or using Splines, that describe complex curves.


# Tesselation
After describing points we need to fix the gaps between them, this is what tesselation is.
Using lines is less complex than using curves.
Each sample is called a vertex, connecting each vertex we can make triangles, because is the simplest polygon that has area.

We can see every connected vertex using a **Wireframe** view.

# Subdivision Surface
Technique for making smoother shapes, by adding a vertex by it's two neighbors and taking the average, multiplying each vertex position by a one-third (or other value) and adding them up. This technique can be parameterized. 
