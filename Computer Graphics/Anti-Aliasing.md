Is a problem with the sampling, creates jagged lines in the border of objects.
Another Problem **Temporal Aliasing**:
When a pixel keeps blinking because of a slight move of an object.

To solve it we can use:
**Supersampling**:
Sending more then one pixel and doing a weighted average of the rays to color the pixel.
Render the object in a higher resolution than, down-sample it. 

**Estimate the fragments coverage**

| Algorithm                                           | Description                                                                         | Pros                                                                  | Cons                                              | Use Cases                                                              |
| --------------------------------------------------- | ----------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------- | ---------------------------------------------------------------------- |
| **SSAA (Super-Sampling Anti-Aliasing)**             | Renders the scene at a higher resolution and downsamples to the desired resolution. | High-quality results, smooths all types of aliasing.                  | Very demanding on performance.                    | High-quality offline rendering.                                        |
| **MSAA (Multi-Sample Anti-Aliasing)**               | Samples multiple points per pixel, but only at the edges (geometry-based).          | Efficient, better quality than basic AA with less performance impact. | Ineffective for shader aliasing and transparency. | Real-time rendering, older game engines.                               |
| **FXAA (Fast Approximate Anti-Aliasing)**           | Post-processing filter that blurs and smooths edges by analyzing pixel contrast.    | Very fast, minimal performance impact.                                | Blurry results, loss of detail.                   | Real-time rendering, consoles, low-end systems.                        |
| **TAA (Temporal Anti-Aliasing)**                    | Combines samples from multiple frames over time to reduce aliasing.                 | Excellent at reducing shimmering and temporal artifacts.              | Can cause ghosting and motion blur.               | Modern game engines, VR, cinematic rendering.                          |
| **SMAA (Subpixel Morphological Anti-Aliasing)**     | Edge detection and subpixel rendering to smooth edges without blurring textures.    | Better quality than FXAA, good performance.                           | Less effective on transparent textures.           | Games, applications needing high-quality AA with low performance cost. |
| **DLSS (Deep Learning Super Sampling)**             | AI-based upscaling method using neural networks trained on high-quality images.     | Excellent quality, improved performance, works well with ray tracing. | NVIDIA hardware required, potential artifacts.    | High-end games, real-time ray tracing.                                 |
| **CMAA (Conservative Morphological Anti-Aliasing)** | A simpler, post-process edge-smoothing technique developed by Intel.                | Better than FXAA, low performance cost.                               | Lower quality than MSAA, TAA, or DLSS.            | Low-end systems, integrated graphics.                                  |
