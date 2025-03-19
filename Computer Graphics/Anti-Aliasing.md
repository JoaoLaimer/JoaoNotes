Is a problem with the sampling, creates jagged lines in the border of objects.
Another Problem **Temporal Aliasing**:
When a pixel keeps blinking because of a slight move of an object.

To solve it we can use:
**Supersampling**:
Sending more then one pixel and doing a weighted average of the rays to color the pixel.
Render the object in a higher resolution than, down-sample it. 

**Estimate the fragments coverage**



