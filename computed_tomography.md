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


**Important:** 

- X-Ray beam is only approximately mono-energetic and attenuation depends on energy  
  **Note:** An x-ray beam consists of many photons. Getting a mono-energetic beam requires all photons to have the same energy level. However, this is not the case in real-world. So, low energy photons will be subject to photoelectric absorption. High energy photons will lose energy and travel further. 

- Effective X-Ray energy increases as it passed through patient. "Beam hardening"  
  If the X-Ray beam hits bone, most of the low energy stuff will get absorbed. The high energy stuff remains.
 
### Beam hardening

Beam hardening occurs when the mean energy of an x-ray beam increases as it passes through an object / patient.  
This is because of the fact that the beam is not mono-energetic. If a low energy photon hits bone, it gets absorbed. The high energy photons travel through. Therefore, the mean energy will obviously increase.

It turns out that beam hardening leads to dark streaks in images.

**Note:** Lower energy photons are attenuated more easily, higher energy photons are attenuated less easily

<img src="images/computed_tomography/beam_hardening.png" width="350" />
  

### Cupping

Cupping means that beams passing through the center are "harded" more than beams passing through edges.

<img src="images/computed_tomography/cupping.png" width="400" />


### Backprojection (Simple)

**Idea:** Let's distribute the values over the attenuation / pixel map.

<img src="images/computed_tomography/backprojection_simple_algo_1.png" width="210" />

<img src="images/computed_tomography/backprojection_simple_algo_2.png" width="290" />

**Problem:** We get a lot of high values! (can also be seen in the example)

**Countermeasures:**

1. Remove the sum in any of the projections (here: 7)  
   <img src="images/computed_tomography/backprojection_simple_algo_3.png" width="150" />
2. Normalize by the highest common factor  
   <img src="images/computed_tomography/backprojection_simple_algo_4.png" width="140" />

   
### How to construct the Hessian Normal Form?

### Backprojection

### Hounsfield units (HU)

We know that our sensor measures energy of photons. Since the energy's range of values is usually really large, we typically have problems to visualize the results. Therefore, we want to apply some kind of normalization.

This is done by Hounsfield units which measure the result with respect to something we know (e.g. attenuation of water).

By doing that we can:

- Minimize the dependence on the energy of x-ray beams
- Produce unit-less values

$HU = 1000 \cdot \frac{\mu - \mu_{H2O}} {\mu_{H2O}}$

**Note:** air = -1000; dense bone = 3000


### Noise and artifacts

__**Quantum noise**__

If multiple photons of different energy levels hit the detector, we obtain slightly varying values. This is also called **quantum noise**.

$SNR = \propto \sqrt{N}$  
N ... number of x-ray quanta/pixel

**Countermeasures:**

- Increase voxel size (reduces resolution)
- Smoothing during reconstruction
- Better quantum efficiency of detector
- "Radiate" longer, but not too long (probably not good for the person ;-)

__**Other effects**__

- Patient motion
- Beam hardening
- Calibration issues
