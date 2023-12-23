# BranchedPolymerCompaction
A framework to build LAMMPS-friendly branched polymer architectures, and then simulate the coil-globule transition through LAMMPS


## Organization

- `/lams` includes all of the files for running the LAMMPS simulations
- `/data` includes all polymer data, broken down by polymer types and then trial. Only trial2 is available here to preserve storage limits (ex. `/data/N1B5/trial2`)
- `BranchedPolymerAnalysis.ipynb` is the notebook summarizing all commands, including a comprehensive analysis pipeline

## Execution 

First, `.lam` files should be run in the command line. 

If using Windows, open the command line, and type 
```
wsl.exe
```
which should either activate or prompt you to download it. 

Then, ensure LAMMPS is run. The executable can be downloaded from [LAMMPS](https://www.lammps.org)
After that's installed, the command line can then run this,
```
env OMP_NUM_THREADS=2 lmp -sf omp -in *.lam

```
where `env OMP_NUM_THREADS=2` attempts to speed up the process by running two simultaneous threads, `lmp` is the base LAMMPS command, `-sf omp` tells lmp that you're using multiple threads, `-in *.lam` inserts the lammps instructions, and * refers to the .lam file name. 

## Contact
Much of this procedure and information is distilled, as a byproduct of research I conducted throughout college. If you'd like more information, feel free to contact me @`cybercyclonedude@gmail.com`!



