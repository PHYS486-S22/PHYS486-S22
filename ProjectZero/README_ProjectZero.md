README: Project Zero
=====================

**Developed by** K. Covey

**Runnable Code:** ProjectZero-Complete.ipynb


Function & Goal
---------
This notebook illustrates how the relative populations of two nuclear species vary with time and as a function of the ratio of their half lifes.  To do this, the notebook loads the core packages + functions that will be used to track the evolution of each population.  The notebook then calculates the evolution of systems with $\gamma$=0.1 and 5, and verifies that they match expectations from the analytic solution to the problem.  Then the notebook calculates the ratio of the population for a range of $\gamma$ values from 0.01 to 100, to understand how the system evolves into its long term state.

Outputs
---------
The main output of this calculation is the figures embedded in the notebook itself.  No tables are produced or saved.


Instructions for Use
---------
To run the code in this notebook using the Google Colab interface:

1. Open the notebook in the GitHub interface
2. Click the 'Open in Colab' button
3. Select 'run all' from the 'Runtime' menu; this will run all cells in the notebook.

**To expand the range of gammas explored in the third figure:** modify the following lines of code in the 9th code cell (with a comment at the top that reads '#now calculate the ratio of NB/NA for various gammas'

```
    #calculate gamma
    gammas[x] = 10.**((x-4)/2)
```

**To change the length of time that the calculation simulates:** modify the value recorded in the 'time_span' variable, in the second active code line of the 9th code cell (as described in more detail above).  
```
time_span = 10.
```


Tests
---------
If all is operating correctly, the first two figures should show that the numerical calcuations and analytic solutions for N$_A$ and N$_B$ agree at all times for the $\gamma$ = 0.1 and 5 cases.


Feedback Requested
---------
I believe the notebook functions correctly, and the calculations are performed accurately and with sufficient numerical precision to meet my project goals.

I would appreciate a quick review of the code to ensure that the above statements are correct, and if there are errors or unacceptable imprecision detected, please let me know!  Otherwise, most useful would be a review of the structure and readability of the notebook.  Suggestions of additional formatting or explanations that could be provided to make the notebook more readable would be very useful.



Key Variables
---------

#### Input parameters

**relative_N<sub>B</sub>** [float, single value, unitless (relative number)]: defines the size of the initial population of species B, relative to the population of N<sub>A</sub> (which has an implicit population size of 1.0. 

**<img src="https://render.githubusercontent.com/render/math?math=\gamma">** [float, single value, unitless (ratio of timescales)]: defines the ratio of the decay timescales of the two species. 

**time_span** [float, single value, unitless (or, equivalently, a time expressed in units of tau<sub>A</sub>)]: the number of half-lives of species A that we want to run the calculation for.

**n_steps** [integer, single value, unitless]: the number of timesteps we should split the simulation's time span into. This implicitly defines the length of each timestep as <img src="https://render.githubusercontent.com/render/math?math=\Delta t="> time_span/n_steps

#### Physical constants
**N<sub>A0</sub>** [float, single value, unitless (relative number)]: defines the size of the initial population of species A - in practice this is set to 1.0.

**tau<sub>A</sub>** [float, single value, unitless (relative time)]: used in the calculation as the half-life/decay timescale of species A, but in practice set to one.  This has the practical implication of implicitly defining our time array to be in units of the actual half-life of species A (which was not set in code -- in retrospect this is probably not a wise choice, but since species A and B aren't defined as true physical species, any value we choose would have to be fictional anyway, so a value of 1.0 is as good as any other made-up value). 

**N<sub>B0</sub>** [float, single value, unitless (relative number)]: defines the size of the initial population of species B, relative to the initial population of N<sub>A</sub>. This value is set by the user specified value of relative_N<sub>B</sub>, but in practice is defined as a new variable to allow the names for the properties of the two species to be perfectly symmetric.

**tau<sub>B</sub>** [float, single value, unitless (relative time)]: the half-life of species B, expressed in units of the half life of species A (or, equivalently, the ratio of those two quantities).  Calculated as tau<sub>A</sub>/<img src="https://render.githubusercontent.com/render/math?math=\gamma"> 


#### Output data
**N<sub>A</sub>** [float, array of length n_steps, unitless (number of atoms, relative to N<sub>A0</sub>)]: An array giving the number of atoms in species A that have yet to decay into species B, expressed as a fraction of the population's initial state.

**N<sub>B</sub>** [float, array of length n_steps, unitless (number of atoms, relative to N<sub>A0</sub>)]: An array giving the number of atoms in species B at a given timestep, expressed as a fraction of the number of species A atoms at the beginning of the simulation (i.e., N<sub>A0</sub>.

**times** [float, array of length n_steps, unitless measure of time (or, equivalently, an actual time measured in units of species' A's half life)]: An array giving the time value that each step in the simulation represents. 


Key Functions
---------
 
**project_populations(N_A0, N_B0, tau_A, tau_B, time_span, n_steps):**

1. creates + fill the array of timesteps
2. calculates the length of each time step as:
  * time_step = time_span / n_steps)
2. creates arrays to store the values of N_A and N_B at each timestep
3. initializes the first element of each array with N_A0 and N_B0.
4. loops over all the timesteps, using the update_populations function to fill the i+1-th elements of the N_A and N_B arrays:

        N_A[i+1], N_B[i+1] = update_populations(N_A[i], N_B[i], tau_A, tau_B, time_step)
  
5. returns the resulting arrays of times, N_A and N_B.
   
**update_populations(N_A, N_B, tau_A, tau_B, time_step)**:

1. calls the calculate_derivatives function to calculate the rate at which each species is decaying:

        dNa_dt, dNb_dt = calculate_derivatives(N_A, N_B, tau_A, tau_B)

2. calculates N_A for the next timestep as 
  * new_Na = N_A + dNa_dt*time_step
3. calculates N_B for the next timestep as
  *  new_NB = N_B + dNb_dt*time_step
4. returns the resulting values for N_A and N_B at the next timestep.

**calculate_derivatives(N_A, N_B, tau_A, tau_B)**:

1. calulates the rate at which atoms of species A are decaying away as
  * dNa_dt = -N_A / tau_A
2. calulates the rate at which species B is gaining atoms (from decays of species A) and losing atoms (from their own decays) as
  * dNb_dt = -N_B / tau_B + N_A / tau_A
3. returns dNa_dt and dNb_dt
