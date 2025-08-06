[[Computer Graphics]]
Each object has its own coordinate systems, we need to transform it to place on the coordinate system of the world. Then we have to place the world to the camera, then the camera to the projection.

Model -> World -> Camera -> Projection

### Transformations

Vector + Vector = Vector
Point + Vector = Point
Point - Point = Vector

- Translation:
	|1 0 0 dx |         |x|
	|0 1 0 dy |  *     |y|     =    Translated Vector
	|0 0 1 dz |         |z|
	|0 0 0 1   |         |1| 
		 w = 0 (vector)
		 w = 1 (point)
- Rotation:
	**X rotation**
	|1  0      0     0 |         |x|
	|0  ca  -sa   0 |  *     |y|     =    Rotated Vector
	|0  sa   ca    0 |         |z|
	|0   0    0      1 |         |w|
	
	**Y rotation**
	|ca  0   sa  0 |         |x|
	|0    1    0   0 |  *     |y|     =    Rotated Vector
	|-sa 0  ca  0 |         |z|
	|0    0   0   1 |         |w|

   **Z rotation** 
	|ca -sa 0 0 |         |x|
	|sa ca  0  0 |  *     |y|     =    Rotated Vector
	|0   0    1  0 |         |z|
	|0   0   0   1 |         |w|

- Scale:
	|dx 0   0   0 |         |x|
	|0   dy 0   0 |  *     |y|     =    Scaled Vector
	|0   0   dz 0 |         |z|
	|0   0   0   1  |        |w|
- Shear:

Affine: preservers ratio of areas
- Translation, Rotation, Non-Uniform or uniform scaling, shearing
Conformal: preserves angles
- Translation, Rotation, Uniform Scaling.
Isometric: preserves length
- Translation, Rotation.
