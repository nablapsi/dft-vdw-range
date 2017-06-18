This git repo contains all resources for the manuscript *The range of semi-local density functionals in van der Waals systems*.

## Requirements

All Python code in the repository requires Python 3.6. The required python packages can be installed with `pip install -r requirements.txt`.

Further, to generate figures and the manuscript:

-   Full LaTeX installation
-   [STIX fonts](http://www.stixfonts.org)

To calculate raw data:

-   [FHI-aims](https://aimsclub.fhi-berlin.mpg.de) for DFT calculations, commit b4905993 (2017-04-05).
-   [Quantum Espresso](http://www.quantum-espresso.org) for VV10 calculations, version 6.1.
-   The [D3 code](http://www.thch.uni-bonn.de/tc/index.php?section=downloads&subsection=getd3) for D3 calculations, version 3.2.
-   The [MBD code](https://github.com/azag0/mbd) for MBD calculations, commit 6a3cde27 (2017-03-17).

## Organization

-   `/pub/`: Contains the LaTeX files that generate the manuscript. The manuscript can be regenerated by running `make`.

- `/media/`: Contains figures used in the manuscript, both generated from the calculated data as well as exported from GUI programs.

- `/src/`: Contains python scripts and Jupyter notebooks used to analyze the data and generate figures. To regenerate all figures and numbers used in the manuscript, evaluate the notebook `/src/2017-05-05-figures.ipynb`.

- `/data/`: This empty directory holds processed data. These can be generated either by running all `/src/collect_*.py` scripts, or downloaded from [here](https://figshare.com/account/articles/5117167).

- `/calc/`: This folder contains all raw calculations organized in four subfolders. Each of them is managed with [Caf](https://github.com/azag0/caf), which is already included individually in each subfolder. With Caf, one can in principle regenerate all inputs files from scratch (the calculations in each subfolder are defined in `cscript.py`), and then use it to run all the calculations to obtain the output files. But this requires nontrivial amount of computational time and is not documented here. Instead, all generated input and output files are provided as tar archives which can be downloaded from [here](https://figshare.com/articles/2017-01-23-all-vdw-sets-3_tar_gz/5117191). The tar archives are unpacked with `tar -xf <archive>` in each subfolder. Once unpacked, the files can be verified by running `./caf status`. The complete directory tree of all input and output files can be checked out with `./caf checkout`.

    Pseudopotentials used in Quantum Espresso, which are not part of the input files, were downloaded from [here](http://www.quantum-espresso.org/pseudopotentials/) and [here](http://www.quantum-simulation.org/potentials/sg15_oncv/).

- `/patches/`: Contains patches of FHI-aims and Quantum Espresso used for the calculations. These would need to be applied if one wanted to recalculate the output files. They are to be applied against the commits stated on the first line of the patches with `patch -p1 <PATCHFILE`.