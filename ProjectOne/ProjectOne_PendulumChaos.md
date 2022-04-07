Project One: Damped Driven Pendulum & the transition to chaotic motion
=====================

**Background + Physics:** A damped (i.e., subject to friction), driven (i.e, subject to a driving force) pendulum can exhibit a wide range of behavior.  Under some combinations of initial conditions (including the magnitude and frequency of its driving force, as well as the magnitude of its damping force), it exhibits regular, periodic motion.  With only small changes to those parameters, however, it can transition into highly unpredictable, chaotic motion. 

If we define the following variables:

* Pendulum's mass: m
* Pendulum's length: l
* acceleration due to gravity: g (=-9.8 m.s -- signs below change if g is assumed to be positive!)
* Pendulum's drive force: <img src="https://render.githubusercontent.com/render/math?math=F(t) = F_0 \rm{sin}(\omega_D t)">
* damping force: <img src="https://render.githubusercontent.com/render/math?math=-q \omega"> 
* restoring force due to gravity:<img src="https://render.githubusercontent.com/render/math?math=-m g l \rm{sin} \theta"> (or, in the small angle approximation, <img src="https://render.githubusercontent.com/render/math?math=-m g l \theta">) 
* pendulum's fundamental frequency: <img src="https://render.githubusercontent.com/render/math?math=\omega_0 = \sqrt{\frac{g}{l}}">


Then we can express the pendulum's equations of motion as:

* <img src="https://render.githubusercontent.com/render/math?math=\delta \theta = \omega">

* <img src="https://render.githubusercontent.com/render/math?math=\delta \omega = - \omega_0^2 \rm{sin} \theta - q \omega">+<img src="https://render.githubusercontent.com/render/math?math=F_0 \rm{sin} (\omega_D t)">

These equations of motion are well suited to a computational approach, but particularly because the system can exhibit chaotic behavior, an integration method with a high level of numerical precision is desirable.  A second order Runga-Kutta (RK-2) integration method usually suffices to capture the system's sensitivity well. 


**Project Scope:** The goal of this project is to a) implement an RK-2 routine and b) use it to construct phase space plots that provide an abstract description of a damped driven pendulum's behavior as it transitions into chaotic motion as the driving force is increased in magnitude. 

A significant fraction of your effort will be devoted to reproducing figures from the text, as a way of verifying that your implementation is working correctly.  In this sense, your deliverables are more extensive, but also more narrowly prescribed, than in other projects.  

This homework is more computationally intensive than the other two options for Project One, requiring a high number of calculations and, based on a typical implementation, a lot of computer memory (i.e., RAM) to store the large arrays/lists that result from those calculations.  Python notebooks are not particularly great at memory allocation, and google colab may not be either: if you are most comfortable working in notebooks, I recommend using a notebook to complete sections a-f, and then once you are sure those pieces are working, copying your routines to a python script that you can use to complete step g.


**Deliverables:**

* Write-up: Your write-up for this problem should be a PDF or markdown file with a number of specific figures to illustrate the correctness of your calculations.  These figures include reproductions of:
    * the plots of <img src="https://render.githubusercontent.com/render/math?math=\theta"> and <img src="https://render.githubusercontent.com/render/math?math=\omega"> vs. time in Figure 3.6 of Giordano & Nakanishi's Computational Physics text.  Try to mimic the formatting (including all three traces in a single panel) if possible.
        * My versions are here:
            * <a href="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/ReplicateFigure3.6.left.png">Figure 3.6, left panel</a>
            * <a href="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/ReplicateFigure3.6.middle.jpg">Figure 3.6, middle panel</a>
            * <a href="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/ReplicateFigure3.6.right.jpg">Figure 3.6, right panel</a> 
    * Figure 3.8 of Giordano & Nakanishi's Computational Physics text, demonstrating the sensitivity of the system to its initial conditions;
        * My versions are here:
            * <a href="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/ReplicateFigure3.8.left.jpg">Figure 3.8, left panel</a>
            * <a href="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/ReplicateFigure3.8.right.jpg">Figure 3.8, right panel</a>
    * the Poincare section (a plot of <img src="https://render.githubusercontent.com/render/math?math=\theta"> vs. <img src="https://render.githubusercontent.com/render/math?math=\omega">) in Figure 3.9 (for F<sub>D</sub> = 1.2 - <a href="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/ReplicateFigure3.9.jpg">my version is here</a>);
    * Additional Poincare sections for F<sub>D</sub>=1.4, 1.44 \& 1.465.  Make sure to remove transient behavior to achieve a clean Poincare section.
    * a full bifurcation diagram for a damped driven pendulum with a driving force coefficient in the range of 1.35 < F<sub>D</sub> < 1.5 (and non-F<sub>D</sub> parameters as given at the end of the caption for Figure 3.6 of Giordano & Nakanishi's Computational Physics text).  <a href="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectOne/Figures/ReplicateFigure3.11.png">My version is here.</a>

	Your write-up should also include a basic discussion of the system and your implementation of it, including:
    
    * the physical model (ie, the forces that affect the pendulum, and how they result in the equations of motion given above), 
    * how you have implemented this model computationally (i.e., an explanation of your RK-2 implementation),
    * how you have established the physical accuracy of your model (ie, tests with known solutions you have performed to demonstrate its accuracy),  
    * explanations of the Poincare sections + bifurcation diagrams you have produced, and what they demonstrate about the system's motion. 

* Along with your write-up, submit a digital copy of your code and high quality copies of your figures (ie, as separate files rather than just embedded in your PDF write-up). 

All of the elements described above (your write-up, your code, and your figures) should be committed to your Project One folder in your Public GitHub repository.  

Note: you will also deliver a few interim products between now and your final project submission (your project plan + psuedocode by April 17th, and working code for a key component of your project by April 24th), but those will be described in separate handouts that apply to all projects.


**Additional Resources:** 

* Chapter 3 of Giordano & Nakanishi's Computational Physics text provides a good treatment of the physics & implementation of a damped driven pendulum and its transition into chaotic motion.  As the problem statement indicates, replicating figures from this text will be an essential component of this project, so you will definitely want to refer to the excerpt I provide of this text.

* A detailed discussion of the dynamics of a damped driven pendulum and its transition to chaotic motion (though without any python code snippets) is given in this write-up by Michael Fowler of the University of Virginia: [Driven Damped Pendulum: Period Doubling, Chaos, Strange Attractors](https://galileoandeinstein.phys.virginia.edu/7010/CM_22a_Period_Doubling_Chaos.html)

* A briefer discussion of a driven (but not damped!) pendulum with some relevant code examples is available in the online text [Learning Scientific Programming With Python](https://scipython.com/blog/the-harmonically-driven-pendulum/)

* an even briefer discussion, but with more relevant python snippets for an actual driven, damped pendulum is also available in this notebook by [Prof. Ligare at Bucknell University](https://eg.bucknell.edu/~phys310/jupyter/chaotic_pendulum.html). 

Remember, it is ok to use these resources, just make sure to cite them in your work!
