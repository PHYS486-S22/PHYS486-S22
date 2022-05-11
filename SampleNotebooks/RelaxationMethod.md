## Relaxation Method Tutorial

As discussed in class, the relaxation method is an algorithm that allows us to find a solution (and thus *the* solution) for a system that satisfies Laplace's equation, where: 

<img src="https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/Figures/Laplace.png" width="300">

Handily, this constraint on the second derivatives of a property will be satisified if the differences between the value of each cell and its neighbors (ie, the slope between a cell and its neighbor) all cancel out.  Conveniently, this is equivalent to saying that we will have a valid solution if and when every cell has a value equal to the average of its neighbors.

So, the method of relaxation just allows us to solve for this equilibrium situation by brute force: maintain the edge of the grid (and any charges within it) at the appropriate boundary conditions, and then sweep through the grid and set each cell equal to the average of its neighbors.  In 3-D, this looks like:

    V[i,j,k] = (1/6) * (V[i-1,j,k] + V[i+1,j,k] + V[i,j-1,k] + V[i,j+1,k] + V[i,j,k-1] + V[i,j,k+1])
    
 And in 2-D, it looks like:
 
    V[i,j] = (1/4) * (V[i-1,j] + V[i+1,j] + V[i,j-1] + V[i,j+1])
 
If we do this over and over again, we will asymptoptically approach the equilbrium state of the grid, and thus the solution to Laplace's equation within its bounds.

I have created a notebook -- [ProjectTwo_Relaxation.ipynb](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/ProjectTwo_Relaxation.ipynb) -- that you can use to explore:
- how the relaxation method works, 
- what it reveals about how the electric field will 'leak' out of a finite capacitor, and 
- how the result you find depends on both the size of the finite capacitor (a physical effect) and the distance between the capacitor and the boundary of the grid (where we are enforcing our boundary condition: a numerical effect). 

The notebook has a series of questions embedded in it for you to explore; I've copied those questions below so that you can make sure you don't miss any, but record your answers in a copy of the notebook itself.

---- 

## IDENTIFY THE PROPERTIES THE SYSTEM + FIELD SHOULD HAVE!

Note that we haven't actually given much indication of the physical properties of our capacitor in the cell above. 

(I say 'much' rather than 'any' because the label on the color bar does reveal that the value of the charges array should have units of volts)

Let's do so now, and identify how we can translate from our numerical units into actual physical values.

### spatial constraints
Assume the capacitor's plates are 20 cm across, and separated by 20 cm as well. 

what is the width of each grid cell?  That is, what are the physical units of $\Delta$x and $\Delta$y?

#### width per grid cell: XXX cm   <--- update this!!!!

### expected E-field

Based on the potential difference and separation between the plates, what do you expect the E-field in the capacitor to be?

#### E-field: magnitude and direction  <--- update this!!!!

---- 

### ATTACHING PHYSICAL UNITS TO THE E-FIELD
The E-field calculation above fundamentally measures the change in potential across two cells at a time.  What does this make the natural units of the plot above?

#### Original units of 'E field strength' in plot above: XXXX <-- Update this!!!

It would be better to convert the plot above to report the E-field strength in the usual units of V/m.  What value do we need to multiply the values in the ey array by to get E-field magnitudes in these units?

#### value to multiply ey by to get field strength in units of V/m: XXXX <-- update this!!!!

Now go ahead and multiply ey by this value and remake the plot above.  Does the peak field strength match your estimate from earlier in the notebook?  Is there any *physical* reason why you might expect it to differ?

----
### Compare to a wider capacitor.

Below are cells that repeat the calculations above. 

### MODIFY THESE CELLS TO SIMULATE A WIDER (40 cm) CAPACITOR 

Re-relax the system, and see how the e-field strength compares
----

You should now have three plots showing the magnitude of the E-field in capacitor's mid-plane in a set of consistent units.

Examine three properties of each plot:
- the strength of the field in the center of the capacitor
- the slope of the E-field where the capacitor's plates end.
- the slope of the E-field at the edge of the grid.

#### write a paragraph explaining what your plots tell you about how those three properties are affected by changes in the size of the capacitor, and separately, the size of the simulation grid.
