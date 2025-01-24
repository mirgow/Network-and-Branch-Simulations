# Network-and-Branch-Simulations
Code Repository for the Article: "Decoding Network Complexity: Harnessing the Power of Simulations to Illuminate Dynamic Interactions in Networks and Branches"

## Organization

| Quick details | -- |
| ----------- | --------- |
| Polymer Types (polymer architectures) |  `Linear` `N1B3` `N1B4` `N1B5` `N3B4` `N5B4` `N7B4` |
| Sea Fan Types (sea fan topologies) | `Tree` `Network` |
| Data Files (LAMMPS-friendly format for seafans or polymers in 3D space) | Polymer: `\dats2` --> `.dat` Sea Fan: `\data` --> `.txt`|
| Log Files [Polymers only] (Storage of LAMMPS output in console, including some measurements) |`\logs` --> `.log` |
| Root Mean Square Distances Files [Polymers only] (`BranchedPolymerANalysis.ipynb` generated RMSD measurements) | `\rmsds` --> `.txt` |
| Mean Square Distances Files [Sea Fans only] (LAMMPS generated MSD measurements) | `\msds` --> `.txt` |
| Trajectories (LAMMPS output simulation information for each polymer) | Polymer: `\trjs` --> `.lammpstrj` Sea Fan: `\trjs` --> `.lammpstrj`|

- `/lams` includes all of the files for running the LAMMPS simulations
- `/data` includes all simulation data, broken down by sea fan morphology or by polymer types and then trial. Only trial2 is available for each polymer type here to preserve storage limits (ex. `Polymers/data/N1B5/trial2`)
- For Polymers, `BranchedPolymerAnalysis.ipynb` is the notebook summarizing all commands, including a comprehensive analysis pipeline
- For Sea Fans, `SeaFansAnalysis.ipynb` is the notebook creating the input data files and performing the analysis

## Seafans Execution

Instructions are below for downloading the softwares used in the project and working with the files in this repository. 

All the simulations are ran with LAMMPS in the command line. The executable for the simulation software can be downloaded from [LAMMPS](https://www.lammps.org), either for Windows or Apple OS. The LAMMPS files have the `.lam` extension and contain information about the force-field, sea fan structure, and timesteps. *Peek at them! There's valuable notes in them for what is running!*

With the software installed well, the simulations can be run with the following command line:

```
lmp_serial -in lammps_file.lam 

```

lmp_serial is the standard LAMMPS command to run on a single processor (which was reasonable for our purpose). LAMMPS can also be built to run in parallel if needed. 

These simulations take, on average, one hour (~2000 atoms, 1000000 timesteps). *Your machine can't stop midway through simulation!*

The output file, which is chosen in the `.lam` file, contains all the information about each atom's position at every timestep. We use this file to run all the analysis in Python. The notebook `SeaFansAnalysis.ipynb` contains the commands needed to generate the data files, read the output data, and perform the analysis.  

## Polymers Execution 

Instructions are below for downloading the softwares used in the project and working with the files in this repository. 

First, `.lam` files should be run in the command line. *Peek at them! There's valuable notes in them for what is running!*

These assume a Windows OS, downloading and working with a Linux Subterminal (Personally worked through Windows Subsystem for Linux 2). Modify accordingly for Apple OS.  

Windows Workflow
1. Ensure Windows Powershell is installed. 
2. Ensure Windows Subsystem for Linux (WSL) is installed. Preferably WSL2. 
3. Activate WSL2. 
```
wsl.exe
Sudo apt-get update
Sudo apt-get install curl
``` 

*COMING SOON: Branched Polymer Generation Script*

Then, ensure LAMMPS is run. The executable can be downloaded from [LAMMPS](https://www.lammps.org)
After that's installed, the command line can then run this,
```
env OMP_NUM_THREADS=2 lmp -sf omp -in *.lam

```
where `env OMP_NUM_THREADS=2` attempts to speed up the process by running two simultaneous threads, `lmp` is the base LAMMPS command, `-sf omp` tells lmp that you're using multiple threads, `-in *.lam` inserts the lammps instructions, and * refers to the .lam file name. 

These simulations can take a while, with the larger n (1000, 1100, 1200) taking upwards of 2-3 hours. *Your machine can't stop midway through simulation!*

Finally, the `BranchedPolymerAnalysis.ipynb` notebook then can be run for all analyses of outputs. 

## Contact
Much of this procedure and information is distilled.
For more information, please contact us authors @`avlad@college.harvard.edu` and @`mihirgwd@gmail.com`.



