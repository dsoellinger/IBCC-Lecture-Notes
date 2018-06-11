## Computed Tomography (CT)

### What's is CT?

We could say that CT is simply rotating x-ray around the human body.

Imagine that we have a human body and a x-ray source to rotates around the human body. The detector captures the remaining x-ray beams once they travelled through the body. We now try to compute the backprojection. Since the scanner (source, detector) rotates and the person moves through the scanner we get many slices. This slices can then be used to reconstruct the person.

<img src="images/computed_tomography/working_principle.png" width="280" />


### Idea of backprojection

Let's assume that the scanner rotates around the patient and while it rotates we capture multiple images.  

<img src="images/computed_tomography/backprojection_multiple_scans.png" width="200" />

The angle and the sampling interval determine the resolution of our reconstructed image. The slice thickness is determined by the collimator opening.

However, how can we now create a 3D reconstruction out of multiple 2D images?  
We can used the **backprojection algorithm.**

To understand the backprojection algorith we need to think about what happens to the x-ray beam when it travels through the body.

<img src="images/computed_tomography/backprojection_computation.png" width="300" />

The remaining intensity of the x-ray beam once it leaves a certain cell can be computed as follows:

$I_{cell,out} = I_{cell,in} \cdot e^{\mu_{cell} \cdot t}$

So, the intensity once it leaves the human body can be computed as follows:

$I_{out} = I_{cell_{n},in} \cdot e^{\mu_{cell_{n}} t}$  
$I_{out} = I_{cell_{n-1},in} \cdot e^{\mu_{cell_{n-1}} t} \cdot e^{\mu_{cell_{n}} t}$  
$I_{out} = I_{cell_{n-2},in} \cdot e^{\mu_{cell_{n-2}} t} \cdot e^{\mu_{cell_{n-1}} t} \cdot e^{\mu_{cell_{n}} t}$  
...  
$I_{out} = I_{in} \cdot e^{\sum {\mu_{i,j}t}}$

Hence, we get:  
$-log(\frac{I_{out}}{I_{in}}) = \sum{\mu_{i,j}t}$

**So, the measured x-ray intensity depends on the sum of attenuation coefficients.**