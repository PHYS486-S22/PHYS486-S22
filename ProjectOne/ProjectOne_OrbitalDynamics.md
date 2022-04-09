Project One: Orbital Dynamics
=====================

**Background + Physics:** Gravitational orbits can be quite complex. Kepler's laws often fool us into thinking that orbits are stable and predictable, but this is an oversimplification - once the perturbations of a third body are introduced, gravitational orbits cannot be described exactly by analytic solutions. Instead, we must calculate the orbits numerically, and when we do, we find that they are chaotic and highly sensitive to initial conditions.

Despite this complexity of behavior, the formalism for calculating gravitational interactions in systems with more than two bodies may be reassuringly familiar. For simplicity, we can confine all objects in our system to a 2-dimensional plane, and place the origin of our coordinate system at the center of mass of the system. Neglecting the third dimension helps avoid lots of complexity, both in coding + in behavior, and placing the origin at the center of mass of the system then allows all bodies in the frame of reference to move freely in response to gravitational forces.  We can then calculate the separation between any two objects in the system as:

<img src="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/separation.png" width="300">

We can then use a Euler Method-like formalism to step the position and velocities of each of the objects in our system forward in time. The 4th order Runga-Kutta method offers better precision, which is often required to model the system for many orbital timescales, but for simplicity we will introduce the formalism below with an Euler-like formalism; those completing this project can do a bit more background reading to understand the issues that may appear with a strict Euler implementation.

In an Euler-like framework, the equations of motion for one object (we'll call it object A) interacting gravitationally with two other objects (we'll call them B and C), can then be projected forward in time as:

<img src="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/vx_equation.png" width="600">

<img src="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/vy_equation.png" width="600">

<img src="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/x_equation.png" width="225">

<img src="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/y_equation.png" width="225">

where the variables in these equations are:

* x and y velocities of object A (and similarly for B+C): v<sub>x,A</sub>, v<sub>y,A</sub> 
* x and y positions of object A (and similarly for B+C): x<sub>A</sub>, y<sub>A</sub>
* object A's mass (and similarly for B+C): M<sub>A</sub> 
* Gravitational constant: G

Once these equations are coded up, the key to simulating a gravitational system is just defining your initial conditions (including the masses and making sure that the net momentum of the system is zero, lest the center of mass drift away from your origin) and letting things run. 

**Project Scope:** The goal of this project is to simulate the Sun-Earth-Moon or Sun-Earth-Jupiter systems, using a framework where the Sun is not fixed at the system's center.  With your calculations, you should investigate a) how precisely energy is conserved in your simulation, over timescales as long as 10,000 years, and b) investigate how the stability of the system(s) are affected if we increase the mass of Jupiter and/or the Moon by factors of 10, 100, and 1000.  

- note: Scipy has a function, ODEint, that handles all the details of the orbit integration under the hood.  That is, I think, out of bounds for this assignment -- it is important to engage the details of how the stepping process occurs and how that affects the orbits that result.  

**Deliverables:**

* Write-up: Your write-up for this problem should be a PDF or markdown file with <10 figures to illustrate the correctness of your calculations and your conclusions regarding the precision of your simulation's ability to conserve energy, and the stability of your solar systems as a function of time.  

	Your write-up should also include a basic discussion of the dynamics and stability of the system, including:
    
    * the physical model (ie, the forces that govern the gravitational interactions, and how they result in the equations of motion given above), 
    * how you have implemented this model computationally (i.e., an explanation of your stepping implementation - to minimize energy issues, I strongly recommend using at least a 4th order Runga-Kutta method with a very small timestep, or a leapfrog/Verlet method to better minimize the energy leak.  Note that examples of both approaches are given below...),
    * how you have established the physical accuracy of your model (ie, tests with known solutions you have performed to demonstrate its accuracy),  
    * explanations of the stability of the system(s) as a function of changes in the mass of the Moon / Jupiter. 

* Along with your write-up, submit a digital copy of your code and high quality copies of your figures (ie, as separate files rather than just embedded in your PDF write-up). 

All of the elements described above (your write-up, your code, and your figures) should be committed to your Project One folder in your Public GitHub repository.  

Note: you will also deliver a few interim products between now and your final project submission (your project plan + psuedocode by April 17th, and working code for a key component of your project by April 24th), but those will be described in separate handouts that apply to all projects.


**Additional Resources:** 

* Chapter 4 of Giordano & Nakanishi's Computational Physics text provides a good introduction to computational implementations of gravitational interactions.  The text walks through how to calculate orbits around a central fixed mass, and provides a roadmap for routines where there are three or more objects, and/or the central object is not fixed. The implementations utilize a Euler-Cromer stepping method; reading Appendix A, which introduces other stepping methods and tests for checking for energy conservation etc, would be beneficial as well.  

* Imad Pasha put together [a nice tutorial](https://prappleizer.github.io/Tutorials/RK4/RK4_Tutorial.html) for coding up orbits with a 4th order Runga Kutta implementation, and in full 3-D to boot!  This does include some reliance on astropy functions to track units, and linear algebra techniques to vectorize the operations, so it may be more than you need, but pedagogically it is a thorough write-up.

* Philip Mocz similarly has a [tutorial](https://medium.com/swlh/create-your-own-n-body-simulation-with-python-f417234885e9) on how to build a compact, 3-D N-body code.  The [code](https://github.com/pmocz/nbody-python) is available on github as well.

* see also the references in the 'Solving ODEs: Methods & Considerations' module on Canvas.

Remember, it is ok to use these resources, just make sure to cite them in your work! 
