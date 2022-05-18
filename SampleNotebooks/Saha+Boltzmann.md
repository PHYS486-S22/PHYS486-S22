## Physical Analysis: Simulating Hydrogen Atoms with a Monte Carlo Markov Chain simulation

**Student Name:** *(if working with a partner, include both names here)*

We've spent time in class exploring how to generate and use random numbers to model statistical processes, like the energy level populations of a hydrogen atom.

As part of this exploration, we worked with a notebook [(Boltzmann.ipynb)](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/Boltzmann.ipynb) that uses a [Markov Chain Monte Carlo](https://machinelearningmastery.com/markov-chain-monte-carlo-for-probability/) approach to evaluate the Boltzmann equation and simulate the energy level populations of a hydrogen gas at a given temperature T. 

We also used this notebook as a basis to practice the Physical Analysis element of expert practice, coming up with some hypotheses we could try to test, and identifying ionization as an important component of the model that was previously missing.

I've now updated the notebook (now called [(Saha+Boltzmann.ipyb](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/Saha%2BBoltzmann.ipynb)) to use the Saha Equation to allow atoms to ionize, which will be indicated in the MCMC chain of energy states as an atom occupying the n=0 state.  

**In this exercise, you will use the [Saha+Boltzmann.ipyb](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/Saha%2BBoltzmann.ipynb) notebook to further practice the Physical Analysis element of expert practice.**

Select one of the hypotheses we developed on Monday, or a new one that you develop today, to explore and test with our updated [Saha+Boltzmann.ipyb](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/Saha%2BBoltzmann.ipynb) notebook.  Copy & edit this file to record your work; when you are done, submit the file back to a ProjectTwo folder in your private GitHub repository.


**Hypothesis:** State the hypothesis you will use the [Saha+Boltzmann.ipyb](https://github.com/PHYS486-S22/PHYS486-S22/blob/main/SampleNotebooks/Saha%2BBoltzmann.ipynb) notebook to confirm or refute.

**Results:** In 2-3 paragraphs, explain the tests you performed and how their results confirm or refute your hypothesis.  

Include in your write-up the evidence from your calculations, summarized either in numerical form, or using figures (e.g., showing energy level populations for a given set of physical inputs).  In presenting this evidence, address the numerical accuracy of your results -- that is, state explicitly how you benchmarked the uncertainties on your numerical results, due to effects like the finite length of your chain, the finite number of energy levels you consider, etc.
