# Preliminaries

Topics covered in this lecture:

- Radiography (X-Ray & CT)
- Magnetic Resonance Tomography (MRT)
- Ultrasound
- Time-of-Flight (ToF)
- Structured Light
- LIDAR

So, this lecture is about imaging modalities __beyond typical "consumer electronics"__.

### Imaging Modalities

**Magnetic Resonance Tomography**

<img src="images/preliminaries/mri_example.png" width="300"/>

__Note:__ Phyical environment (temperature, scanner parameters, etc.) has a huge impact on the captures image. Which means that an image of the same person might look different captures a second time.

**Computer Tomography**

<img src="images/preliminaries/ct_example.png" width="300"/>

__Note:__ Captured by "rotating X-Ray".

**Problem with CT:**  
Ionizing ("ionisierend") radiation is typical used for more "bone-like" structures. Means it's hard to differentiate between many different tissue types. MRT is always us to better differentiate between different tissue types.

**Ultrasound**

<img src="images/preliminaries/ultrasound_example.png" width="300"/>

**Structured Light**

<img src="images/preliminaries/structured_light_example.png" width="300"/>

We get two different types of information:   
- Point Cloud  
- Depth Map


### Intensity values

Intensity values are related to physical tissue characteristics.  
So the actual value of an image has more meaning that in standard imaging.

### Anatomical Orientations

<img src="images/preliminaries/orientation_definition.png" width="400"/>

Orientations are typically encoded in a three letter code. We need to be really careful since different images can have totally diferent letter codes!

**The code always describes to positive direction of each axis!**  

**Example: RAS**  
R: x-axis from left to right  
A: y-axis from posterior to anterior  
S: z-axis from interior to superior  

**Imaging Planes**  
  
<img src="images/preliminaries/anatomy.png" width="400"/>

**Coordinate Space**

We have multiple coordinate systems:

- **World:** How the patient was "laying" within the scanner.
- **Anotomical:** Coordinate system with respect to the planes
- **Image:** Coordinate system of the image

**Note:** In some cases we have to go back from the image coordinate system to the world coordinate system. For instance, we have a robot which operates a patient. Brain surgery

**Image Origin**  
Position of the first voxel in the anatomic coordinate space.

origin = [100mm, 50mm, -10mm]

**Voxel spacing**  
Distance between voxel.

spacing = [1mm, 1mm, 0.9mm]

<img src="images/preliminaries/spacing_example.png" width="100"/>

**Note:** If want to see a lot of details (very small structures), I need a fine spacing, otherwise I'm not able to capture all the details.


### What's a imaging phantom?
An imaging phantom for determining CT performance
Imaging phantom, or simply phantom, is a specially designed object that is scanned or imaged in the field of medical imaging to evaluate, analyze, and tune the performance of various imaging devices. For example, we can use a phantom to calibrate your device.


