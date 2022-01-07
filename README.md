# Microstate Analysis of Protein
This is the tutorial for microstate analysis in the Monte Carlo Sampling.  In this tutorial, lysozyme 4lzt at pH = 7 is used.  

# Introduction:
Proteins are dynamic objects and it is well established that they exist in a distribution of conformations.  Conformationaion distributions are required for function, but they are also inevitable given the low barriers to many of the motions proteins can undergo. Thus, a protein with N atoms has 3N-6 vibrational modes to generate the conformational flexibility.       
Monte Carlo sampling in MCCE uses Metropolis–Hastings algorithm to evaluate the microstate probability distribution. A microstate step is achieved by a residue conformer flip, that is, the conformer of a randomly chosen residue is switched to another conformer of its residue. Multi-flip is performed at 50% chance if some conformers of the chosen residue have big interactions with conformers in other residues. This is to allow concerted motion/ionization to have a fair chance to be evaluated. The Monte Carlo sampling in MCCE goes through annealing stage, reduction stage, and sampling stage. The annealing stage is to gradually reduce the temperature in the Boltzmann distribution function to the room temperature. This will ensure the statistics of microstates are only collected at the equilibrium even though the first randomly selected microstate may be quite off the equilibrium.   The reduction stage is to sample the microstates for a fair number of steps. The conformers that are never appeared in reduction stage are excluded from later sampling. After reduction, residues that have choice of conformers are “free” residues. Only in the sampling stage, the conformer occupancy and optionally the microstates are recorded.



## Input File:
- head3.lst 
- ms_out file

### ms_out file information
One of the big challenges is recording all possible millions of microstates in readable format. MCCE algorithm has several approximations that are advantageous for the microstate analysis.  One is that conformers are premade so that we can label them for each microstate.  Also, that only a few residues are changed on each step so that we need to only record the conformers that have changes when a microstate is accepted. In the beginning of file, fixed conformers and free conformers ids are saved. In first line of each Monte Carlo run, microstates of free conformers residues are recorded and the following each line in each step have information of enthalpy (Kcal/Mol) of system, total number of times that microstate stuck before accepting the new state called count, and conformers ids of residues that are flipping.


## Script requirement:
  - ms_analysis.py: This script loads the input file.
  - weighted_correlation.py: This is to find the weighted correlation coefficient
  - microstate_analysis.ipynb : This is for post processing of microstates.
  
  
