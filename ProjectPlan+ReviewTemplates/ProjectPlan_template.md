Project Plan Template
=====================

**Developed by** Name

> By the time you are wrapping up your project, you may find yourself running a routine that automates the full set of calculations you will need to analyze to understand the physical phenomoneon in question.  For instance, you may find yourself repeating calculations of projectile motion, a pendulum trajectory, or gravitational orbits, with slightly different input parameters.  
> 
> For this exercise, you should plan out a set of routines that would run one of those projectile/pendulum/orbit calculations. The properties that you will need to vary over multiple calculations should be specified as input parameters, and your routine should output the information you would need to do your final analysis (i.e., the time difference between drag and no-drag trajectories; the fixed points of a pendulum for a given driving force; or the energy precision + stability timescale for a given orbital configuration).  

Goal
---------
>always good to start with the end in mind: write 2-3 sentences here to remind yourself and your reader what this routine is hoping to calculate, and why.


Variables
---------

#### Input parameters

> List here any parameters that would vary from calculation to calculation.  Specify the name you will give the variable, what it encodes, the physical units, the data type (float/integer/string, stored as a single value or an array), and what values you expect the routines to receive. 


#### Physical constants
> List here any physical or numerical constants that you will need to perform your calculation, but which you do not expect to vary (so can be encoded within the routine itself). Specify the name you will give the variable, what it encodes, the data type (float/integer/string, stored as a single value or an array), and the value and physical units you will define it with. 


#### Output data
> List here the data that your routine will need to return to enable your analysis.  Specify what the data will mean, what data type (float/integer/string, stored as a single value or an array) you will store it in, and the physical units you will adopt for those values. Note that the units you plan adopt should be informed by the magnitude of the values you expect to compute -- it is awkward to express a year as 10<sup>7</sup> seconds, for example...


Routine Outline
---------

> Here, outline your strategy for performing your calculation, using a combination of function definition + return statements (which illustrate the type of data the function will recieve and return), and psuedocode (to illustrate how the function will work).
> 
> Start with psuedocode for the highest level processing you plan to do, and include functions/subroutines at the bottom of that outline.  Python would not like this ordering, but your human reviewer will likely find it easier to review your plan if they see the high level strategy first, and then can dive into the detailed logic for subroutines later. 
>
>As an example of what this might look like in practice, see this [example project plan](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/ProjectPlan%2BReviewTemplates/ProjectPlan_ProjectZero.md) for the nuclear decay code in the Project Zero notebook...