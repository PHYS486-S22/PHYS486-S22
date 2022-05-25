## Physical Analysis: Analyzing the behavior of a particle in a finite well

**Student Name:** *(if working with a partner, include both names here)*

We've spent time in class examining how we can use linear algebra to solve the Schrodinger equation.

As part of this exploration, we worked with a notebook to use numpy's built in linear algebra capability to solve the Schrodinger Equation for a infinite square well [(Solving_the_Schrodinger_Equation_Numerically.ipynb)](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/Schrodinger/Solving_the_Schrodinger_Equation_Numerically.ipynb). Since the infinite square well can be solved analytically, being able to demonstrate that the numerical solution agrees with the analytic predictions was useful for validating that the method was sound. 

We then explored how to use the method to solve for the wavefunctions in a finite square well, and in [a follow-up notebook](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/Schrodinger/Linear%20Potential%20in%20QM.ipynb), used the method to explore finite wells with more interesting geometries.  Last friday, the notebook had two examples: finite wells where the potential was a linear function, either symmetric about zero or one-sided with a vertical wall at zero.  Since Friday, I've fixed (I hope!) all the python 2 syntax issues, and added a third potential with several periodic barriers.

**In this exercise, you will use this [Linear Potential in QM](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/Schrodinger/Linear%20Potential%20in%20QM.ipynb) notebook to further practice the Physical Analysis element of expert practice.**

The assignment involves two analyses:

The first task is to examine the behavior of the wavefunctions in the third potential I have added to the notebook, and determine if they appear to be physically correct solutions to Schrodinger's equation in the potential in question.

The second task is to analyze the allowed wavefunctions in a new, fourth potential that you add to the notebook. In thinking about what type of potential you should add, try to identify a potential that has a significant difference in shape from the potentials already present in the notebook.  

Prompts to report out these analyses are below.  Copy & edit this file to record your work; when you are done (or by Wednesday, June 1st, whichever comes first), submit the file back to a ProjectTwo folder in your private GitHub repository.


**Analysis of allowed wavefunctions in a finite well with periodic barriers:** Do the wavefunctions shown as solutions for the potential with periodic barriers appear physically accurate?  Why or why not?  Try to include at least two specific aspects of the wavefunctions' behavior that informs your judgement.


**Description of newly added potential:** Describe in words (or with an embedded equation) the new potential that you chose to explore solutions of Schrodinger's equation in.  Create and attach/embed a figure to illustrate this new potential, and highlight in your description any aspects of the potential that are particularly different from the other inifite and finite square wells for which you've studied solutions of Schrodinger's equation.

**Analysis of allowed wavefunctions in your newly added potential:** In 1-2 paragraphs, describe the behavior of the allowed wavefunctions in the new potential you are exploring.  Create and attach/embed a figure to illustrate the allowed wavefunctions, and highlight in your description any aspects of their behavior that conform with, or are counter to, your physical intuition for what the allowed solutions should be in this potential. 

**Optional analysis of allowed wavefunctions in your newly added potential:** If you have time and energy, try also varying aspects of the potential -- the width, depth, shape, etc. -- in a systematic way, and describe how the allowed wavefunctions vary in response to these changes.  This really is optional, but might be fun!  
