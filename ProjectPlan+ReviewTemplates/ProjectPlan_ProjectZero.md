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


Routine Outline
---------

1. Initialize input variables (in retrospect, should/could have made a wrapper function that took in the variables + the filename for saving the resultant plot)

2. Calculate all implicitly defined physical constants (i.e., tau_A, tau_B, N_A0, N_B0).

3. call a function (project_populations) that runs the simulation.    
    This function will be called as:
    
        time, N_A, N_B = project_populations(N_A0, N_B0, tau_A, tau_B, time_span, n_steps)
        
    and returns arrays with the time, N_A and N_B of each timestep in the simulation.

4. Plot N_A vs. time and N_B vs. time to examine evolution of system

5. (in practice the notebook then looped over several values of gamma and made a summary plot, but this is the kind of parameter variation that I have suggested to leave out of an initial planning process).    

--- functions ---    

**project_populations(N_A0, N_B0, tau_A, tau_B, time_span, n_steps):**

1. create + fill the array of timesteps
2. calculate the length of each time step as:
  * time_step = time_span / n_steps)
2. create arrays to store the values of N_A and N_B at each timestep
3. initialize the first element of each array with N_A0 and N_B0.
4. loop over all the timesteps, using the update_populations function to fill the i+1-th elements of the N_A and N_B arrays:

        N_A[i+1], N_B[i+1] = update_populations(N_A[i], N_B[i], tau_A, tau_B, time_step)
  
5. return the resulting arrays of times, N_A and N_B.
   
**update_populations(N_A, N_B, tau_A, tau_B, time_step)**:

1. call the calculate_derivatives function to calculate the rate at which each species is decaying:

        dNa_dt, dNb_dt = calculate_derivatives(N_A, N_B, tau_A, tau_B)

2. calculate N_A for the next timestep as 
  * new_Na = N_A + dNa_dt*time_step
3. calculate N_B for the next timestep as
  *  new_NB = N_B + dNb_dt*time_step
4. return the resulting values for N_A and N_B at the next timestep.

**calculate_derivatives(N_A, N_B, tau_A, tau_B)**:

1. calulate the rate at which atoms of species A are decaying away as
  * dNa_dt = -N_A / tau_A
2. calulate the rate at which species B is gaining atoms (from decays of species A) and losing atoms (from their own decays) as
  * dNb_dt = -N_B / tau_B + N_A / tau_A
3. return dNa_dt and dNb_dt
