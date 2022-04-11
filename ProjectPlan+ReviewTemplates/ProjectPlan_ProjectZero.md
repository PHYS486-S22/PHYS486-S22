Project Plan: Project Zero
=====================

**Developed by** K. Covey

Goal
---------
This routine will calculate the relative populations of two nuclear species as a function of time. We will initialize the calculation with their initial relative populations and decay timescales, as well as the duration of the calculation and the number of timesteps we should split that duration into (which implicitly sets the length of each timestep).  The output of this calculation will allow us to understand how the system evolves with time, and eventually compare its endstate (or its rate of change) with other systems with different initial abundances or relative decay timescales. 


Variables
---------

#### Input parameters

**relative_N<sub>B</sub>** [float, single value, unitless (relative number)]: defines the size of the initial population of species B, relative to the population of N<sub>A</sub> (which has an implicit population size of 1.0. 

**<img src="https://render.githubusercontent.com/render/math?math=\gamma">** [float, single value, unitless (ratio of timescales)]: defines the ratio of the decay timescales of the two species. 

**time_span** [float, single value, unitless (or, equivalently, a time expressed in units of tau<sub>A</sub>)]: the number of half-lives of species A that we want to run the calculation for.

**n_steps** [integer, single value, unitless]: the number of timesteps we should split the simulation's time span into. This implicitly defines the length of each timestep as <img src="https://render.githubusercontent.com/render/math?math=\Delta t="> time*_*span/n*_*steps

#### Physical constants
**N<sub>A0</sub>** [float, single value, unitless (relative number)]: defines the size of the initial population of species A - in practice this is set to 1.0.

**tau<sub>A</sub>** [float, single value, unitless (relative time)]: used in the calculation as the half-life/decay timescale of species A, but in practice set to one.  This has the practical implication of implicitly defining our time array to be in units of the actual half-life of species A (which was not set in code -- in retrospect this is probably not a wise choice, but since species A and B aren't defined as true physical species, any value we choose would have to be fictional anyway, so a value of 1.0 is as good as any other made-up value). 

**N<sub>B0</sub>** [float, single value, unitless (relative number)]: defines the size of the initial population of species B, relative to the initial population of N<sub>A</sub>. This value is set by the user specified value of relative*_*N<sub>B</sub>, but in practice is defined as a new variable to allow the names for the properties of the two species to be perfectly symmetric.

**tau<sub>B</sub>** [float, single value, unitless (relative time)]: the half-life of species B, expressed in units of the half life of species A (or, equivalently, the ratio of those two quantities).  Calculated as tau<sub>A</sub>/<img src="https://render.githubusercontent.com/render/math?math=\gamma"> 


#### Output data
**N<sub>A</sub>** [float, array of length n_steps, unitless (number of atoms, relative to N<sub>A0</sub>)]: An array giving the number of atoms in species A that have yet to decay into species B, expressed as a fraction of the population's initial state.

**N<sub>B</sub>** [float, array of length n_steps, unitless (number of atoms, relative to N<sub>A0</sub>)]: An array giving the number of atoms in species B at a given timestep, expressed as a fraction of the number of species A atoms at the beginning of the simulation (i.e., N<sub>A0</sub>.

**times** [float, array of length n_steps, unitless measure of time (or, equivalently, an actual time measured in units of species' A's half life)]: An array giving the time value that each step in the simulation represents. 


Routine Outline
---------

1. Initialize input variables (in retrospect, should/could have made a wrapper function that took in the variables + the filename for saving the resultant plot)

2. Calculate all implicitly defined physical constants (i.e., tau*_*A, tau*_*B, N*_*A0, N*_*B0).

3. call a function (project*_*populations) that runs the simulation.    
    This function will be called as:
    
        project_populations(N_A0, N_B0, tau_A, tau_B, time_span, n_steps)
        
    and will return arrays with the time, N*_*A and N*_*B of each timestep in the simulation.
    

--- functions ---    

**project*_*populations(N*_*A0, N*_*B0, tau*_*A, tau*_*B, time*_*span, n*_*steps):**

1. create + fill the array of timesteps
2. create arrays to store the values of N*_*A and N*_*B at each timestep, and initialize the first element of each array with N*_*A0 and N*_*B0.
3. loop over all the timesteps, filling the arrays of  N*_*A and N*_*B with outputs of the update*_*populations() function
4. return the resulting arrays of times, N*_*A and N*_*B.
   
**update*_*populations(N*_*A, N*_*B, tau*_*A, tau*_*B, time*_*step)**:

1. call the calculate*_*derivatives function to calculate the rate at which each species is decaying (which will be returned as dNa*_*dt and dNB*_*dt).
2. calculate N*_*A for the next timestep as 
  * new*_*Na = N*_*A + dNa*_*dt*time_step
3. calculate N*_*B for the next timestep as
  *  new*_*NB = N*_*B + dNb*_*dt*time_step
4. return the resulting values for N*_*A and N*_*B at the next timestep.

**calculate*_*derivatives(N*_*A, N*_*B, tau*_*A, tau*_*B)**:

1. calulate the rate at which atoms of species A are decaying away as
  * dNa*_*dt = -N*_*A / tau*_*A
2. calulate the rate at which species B is gaining atoms (from decays of species A) and losing atoms (from their own decays) as
  * dNb*_*dt = -N*_*B / tau*_*B + N*_*A / tau*_*A
3. return dNa*_*dt and dNb*_*dt