## Image Registration

### Goal

Let' say that we have to images (e.g. images of a human brain).  
We now want to find a transformation T that maps image A to image B.

For instance, this comes in handy if we have an annotated brain ATLAS and a set of new images which are not annotated. By finding the right transformation we can easily annotated the new images.

**Note:** An ATLAS is typically not constructed from a single patient only. Instead images of multiple patients of a certain age group get averaged.


### Rigid Transformation

<img style="float: right; margin-right: -2

0px; margin-top: 10px;" src="images/image_registration/rotation_translation_reflection.png" width="150"/>

A rigid transform is a geometric transformation that **preserves distances**.  
It includes **rotations, translations, reflections**.

$x' = Rx + t$

where 

R ... is the rotation matrix  
x ... is a point in $R^2$ or $R^3$  
t ... is a translation vector

and R is an orthogonal transformation ($R^T = R^{-1}$).

Furthermore, we differentiate between **proper** and **improper** transformations.  
A transformation is called **proper**, if the determinante of $det(R)=+1$ which means that it rotates and translates only.  
**Improper** translations can reflect, translate and rotate. In such a case $det(R)=-1$.

We can define a *proper* translations as a concatenation of multiple rotations.

<img src="images/image_registration/proper_rotation_example.png" width="500"/>

As we can see the rigid transform has 6 parameters. We have 3 degrees of freedom ($\alpha$, $\beta$, $\gamma$) and 3 translation parameters.

**Note:** Rigid transforms which include translation are NOT linear transforms.

In **homogeneous coordinates** we can write a rigid transformation as **one matrix multiplication**.


### Rigid + Scaling Transformation

The simplest non-rigid transformation is rigid + scaling. It's define as follows:

$x' = RSx + t$

with 

$S_x = \begin{pmatrix} r_x & & 0 \\ 0 & r_y & 0 \\ 0 & 0 & r_z\end{pmatrix}$ 

Obviously, distances are not longer preserved.

**Caution:** $x' = SRx + t$ produces a different result. 

In case scaling is isotropic (equal in all dimensions), we speak of a **similarity transform**.


### Affine Transformation

Scaling transformations are special cases of the more general class of **affine transformations**. Affine transformations are defined as follows:

$x' = Ax + t$

where there is no restriction on the elements of A. **Affine transformations** preserve

- straight lines (and hence, the planarity of surfaces)
- parallelism

There is no restriction on A. It can be anything.

### Projective Transformation

The projective transformation can be written as:

$x' = \frac{Ax+t}{<p,x> + \alpha}$.

Only straight lines and planar surfaces are preserved.

### Image Registration

**Algorithm:**

Let's say we have two volumes (images) A and B. Volume A is called the *fixed image* since it does not move. Volume B is called the *moving image* since it's the one we apply the transform on.

1. Take an initial transform and transform volume A (fixed image).  
   Perform interpolation if needed (in case we are not on real integer coordinates).
2. Take a cost function (e.g. sum-of-squared-differences) and compute the similarity between the transformed image and volume B.
3. 
