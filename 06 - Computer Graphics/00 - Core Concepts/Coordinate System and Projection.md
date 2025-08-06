[[Computer Graphics]]
Two Classes of Planar Geometric projections
a) Perspective: determined by Center of Projection (COP),
Can be your eye or the camera.
- Human visual system.
- Pros: gives a realistic view.
- Cons: does not preserve shape and scale of object
- Can have more than one point of perspective.

b) Parallel: determined by Direction of Projection (DOP), do not converge to a point, COP is at infinity.
- Projection are determined by the direction of the projection plane.
- Used for: engineering drawings, architectural drawings.
- Pros: accurate measurement.
- Cons: does not provide realistic view or sense of 3D form.


### Camera
- Frustum: The area visible after the view plane.
Camera as a model: we usually move the world.
We create a matrix for the camera and move it to the origin, moving the world with it so it relates to the camera.

**Camera Matrix**

| Ux  Uy  Uz  -Cx |
| Vx  Vy  Vz  -Cy  |
| Wx Wy Wz -Cz  |
| 0    0    0      1     |

1. Position of the camera
2.  Look Vector
	Points to where the camera is looking.
3.  Up Vector
	Determines the rotation of the camera. Is never parallel to the Look vector.
4.  Aspect ratio
	 Ratio of width to height displayed on screen.
5.  View angle
	Determines the amount of perspective distortion, from no distortion (parallel projection) to high distortion (wide-angle lens)
6.  Near and Far Clipping Planes
	 Used to bound the frustum with a front and back plane. Anything not between the near and far plane is discarded or clipped.

**Camera Coordinate System**
The equivalent x,y,z in camera space are the unit vectors u,v and w.
w is a unit vector in the opposite direction of the look vector.
v is the part of the up vector perpendicular to the look vector.
u is perpendicular to both v and w.

w = -lookV / |lookV| 

u =  upV X w / |upV X w|
	X is cross-product.
v = w X u
