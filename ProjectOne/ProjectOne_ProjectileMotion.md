Project One: Realistic Projectile Motion
=====================

**Background + Physics:** Most introductory physics courses neglect the drag force when performing projectile motion problems, as coupling the acceleration to the velocity makes simple analytic solutions to the equations of motion difficult to obtain.  

With a computer, however, that coupling can be accounted for in a  straightforward manner. The acceleration due to drag can be calculated as:

<img src="https://render.githubusercontent.com/render/math?math=\vec{a_{drag}} = - \frac{C A \rho v^2}{2 m} \hat{v}">

where C is the drag co-efficient of the object in question, A is the object's cross sectional area, <img src="https://render.githubusercontent.com/render/math?math=\rho"> is the density of the medium the object is moving through, v is its total 2-D velocity, and the <img src="https://render.githubusercontent.com/render/math?math=\hat{v}"> term demonstrates that the acceleration will operate to oppose the direction of motion. 

While the acceleration due to drag will be aligned with the projectile's direction of motion, which may have both x and y components, the acceleration due to gravity will only have a y component.  This will necessitate calculating the x and y components of the acceleration due to drag, and applying them to the object's x and y velocities separately. 




**Project Scope:** Consider two identical objects that start at the same height above the ground.  One object is dropped, but the other is launched at an angle <img src="https://render.githubusercontent.com/render/math?math=\theta"> with respect to the horizontal.  Including air resistance, which object hits the ground first?  

In this project, your task is to quantify how the time difference between the two objects hitting the ground depends on the parameters of the object (mass, surface area & drag co-efficient) and the launch conditions (initial velocity, initial height, and angle with respect to the hortizontal). 

Reduce the dimensionality of the problem if possible (ie, combine parameters that have the same impact into a single variable, as we used the variable <img src="https://render.githubusercontent.com/render/math?math=\gamma"> to express the ratio of the time constants in Project Zero instead of varying them independently).  Summarize the behavior for launch angles of 0, 25, 50 and 75 degrees with respect to the horizontal, and explore at least three orders of magnitude in the object's parameters, initial velocity, and initial height.  


**Deliverables:**

* Write-up: Your write-up for this problem should be a <6 page PDF file (or a markdown file of comparable length when rendered) with no more than 6 figures.  Your write-up should discuss:
    * the physical model (ie, how drag + projectile motion work), 
    * how you have implemented this model computationally, 
    * how you have established the physical accuracy of your model (ie, tests with known solutions you have performed to demonstrate its accuracy - replicating figures 2.4 or 2.5 in Giordano & Nakanishi can be a good confidence builder, for instance),  
    * how you have validated the numerical precision of your calculations (i.e., convergence tests performed), and
    * your results, with qualitative and quantitative conclusions regarding the dependence of the time difference on the parameters of the projectile and the conditions that describe the launched state. \\ 

* Along with your write-up, submit a digital copy of your code and a tab delimited ascii table providing the x and y positions as a function of time for a 100 kg sphere with a cross-sectional area of A=0.1 m<sup>2</sup> launched from a height of y=10<sup>3.5</sup> m with v<sub>x</sub>=10 m/s.  For this calculation, assume a drag coefficient of C=0.5 and a density of air of <img src="https://render.githubusercontent.com/render/math?math=\rho">=1.225 kg \ m<sup>3</sup>. For this table, follow the format given below, where time and distance expressed in units of seconds and meters, respectively. 

| time (sec) | x (m) |   y (m) | 
| ---------- | ----- | ------- |
|    0.0     |  0.0  | 3162.28 |
|    ...     |  ...  |   ...   |
|    3.0     | 29.598| 3118.68 | 

All of the elements described above (the PDF of your write-up, your code, and your numerical table) should be committed to your Project One folder in your Public GitHub repository.  

Note: you will also deliver a few interim products between now and your final project submission (your project plan + psuedocode by April 17th, and working code for a key component of your project by April 24th), but those will be described in separate handouts that apply to all projects.


**Additional Resources:** 

* Chapter 2 of Giordano & Nakanishi's Computational Physics text provides a good treatment of the physics & implementation of 2-D projectile motion with drag.

* A treatment of projectile motion with quadratic drag, including some relevant code examples, is available in the online text  [Learning Scientific Programming With Python](https://scipython.com/book2/chapter-8-scipy/examples/a-projectile-with-air-resistance/)

Remember, it is ok to use these resources, just make sure to cite them in your work!
