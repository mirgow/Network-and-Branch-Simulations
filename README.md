# BranchedPolymerCompaction
A framework to build LAMMPS-friendly branched polymer architectures, and then simulate the coil-globule transition through LAMMPS


## Organization

| Quick details | -- |
| ----------- | --------- |
| Polymer Types (polymer architectures) |  `Linear` `N1B3` `N1B4` `N1B5` `N3B4` `N5B4` `N7B4` |
| Data Files (LAMMPS-friendly format for polymers in 3D space) | `\dats2` --> `.dat` |
| Log Files (Storage of LAMMPS output in console, including some measurements) | `\logs` --> `.log` |
| Root Mean Square Distances Files (`BranchedPolymerANalysis.ipynb` generated RMSD measurements) | `\rmsds` --> `.txt` |
| Trajectories (LAMMPS output simulation information for each polymer) | `\trjs` --> `.lammpstrj` |

- `/lams` includes all of the files for running the LAMMPS simulations
- `/data` includes all polymer data, broken down by polymer types and then trial. Only trial2 is available here to preserve storage limits (ex. `/data/N1B5/trial2`)
- For each polymer type
- `BranchedPolymerAnalysis.ipynb` is the notebook summarizing all commands, including a comprehensive analysis pipeline

## Execution 

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
Much of this procedure and information is distilled, as a byproduct of research I conducted throughout college. If you'd like more information, feel free to contact me @`cybercyclonedude@gmail.com`!



