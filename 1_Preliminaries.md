# Preliminaries

Topics covered in this lecture:

- Radiography (X-Ray & CT)
- Magnetic Resonance Tomography (MRT)
- Ultrasound
- Time-of-Flight (ToF)
- Structured Light
- LIDAR

In other words, this lecture is about imaging modalities __beyond typical "consumer electronics"__.

### Imaging Modalities

**Magnetic Resonance Tomography**

<img src="images/preliminaries/mri_example.png" width="300"/>

__Note:__ The physical environment (temperature, scanner parameters, etc.) has a huge impact on the resulting image. Therefore, it can easily happen that images of the same patient captured over a certain period of time look different.

**Computer Tomography**

<img src="images/preliminaries/ct_example.png" width="300"/>

__Note:__ Captured by "rotating X-Ray".

**Problem with CT:**  
Ionizing ("ionisierend") radiation is typical used for "bone-like" structures. It's hard to differentiate between many different tissue types. MRT performs much better in these types of scenarios.

**Ultrasound**

<img src="images/preliminaries/ultrasound_example.png" width="300"/>

**Structured Light**

<img src="images/preliminaries/structured_light_example.png" width="300"/>

We get two different types of information:   
- Point Cloud  
- Depth Map


### Intensity values

Intensity values are related to physical tissue characteristics.  
In this sense, we could also say that say that the voxel value in medical imaging has more meaning than in standard imaging.

### Anatomical Orientations

<img src="images/preliminaries/orientation_definition.png" width="400"/>

Orientations are typically encoded in a three letter code. We need to be really careful since different images often have totally different letter codes!

**The code always describes the positive axis' direction!**  

**Example: RAS**  
R: x-axis from left to right  
A: y-axis from posterior to anterior  
S: z-axis from interior to superior  

**Imaging Planes**  
  
<img src="images/preliminaries/anatomy.png" width="400"/>

**Coordinate Space**

We have multiple coordinate systems:

- **World:** How the patient was "lying" within the scanner.
- **Anotomical:** Coordinate system with respect to the planes
- **Image:** Coordinate system of the image

**Note:** In some cases we have to go back from the image coordinate system to the world coordinate system. For instance, if we have a robot which operates a patient (e.g. rain surgery)

**Image Origin**  
Position of the first voxel in the anatomic coordinate space.

origin = [100mm, 50mm, -10mm]

**Voxel spacing**  
Distance between voxel.

spacing = [1mm, 1mm, 0.9mm]

<img src="images/preliminaries/spacing_example.png" width="100"/>

**Note:** If want to see a lot of details (very small structures), we need a fine spacing. Otherwise we are not able to capture all the details.


### What's a imaging phantom?
Imaging phantom, or simply phantom, is a specially designed object that is scanned or imaged in the field of medical imaging to evaluate, analyze, and tune the performance of various imaging devices. For example, we can use a phantom to calibrate your device.


