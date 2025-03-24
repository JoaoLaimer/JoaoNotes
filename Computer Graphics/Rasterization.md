[[Computer Graphics]]
The screen is a discrete grid where the elements are pixels. We need to convert the geometry to pixels. Rasterization is the process of selecting the pixels to draw.
Is done frequently.
**Line Drawing**
- Bresenham's algorithm:
Conditions:
- Length of X > Length of Y (Delta)
- x0 < x1
- y0 <= y1
- -1 < slope < 0

	if | Dy | > | Dx|
		swap(x0, y0)
		swap (x1, y1)
	if x0  > x1
		swap(x1, x0) 
	Epsilon = | DeltaY / DeltaX |
	From x <- |x0| to x <= x1
		if |Dy| > |Dx|
			plot(y,x)
		else
			plot(x,y)
		DeltaE <- DeltaE + E
		if DeltaE >= 0.5
			if |Dy| > |Dx|
				y <- y -1
			else
				y <- y +1
			DeltaE <- DeltaE - 1

To get the conditions we can swap x with y.

- Linear Interpolation
	Interpolates colors between two vertices.
- Bilinear Interpolation
	Interpolates between two Linear Interpolation.
Both are combined to create a gradient in a 2D plane.

**Anti-Aliasing**
Smooth the pixels in a line.
