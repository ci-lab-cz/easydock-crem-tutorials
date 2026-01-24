# EasyDock & CReM Setup

## Overview

**EasyDock** is a tool for fully automated high-throughput molecular docking and serves as the backbone of several *de novo* design tools developed on top of **CReM**. All these tools are part of an ecosystem of automated open-source chemoinformatics pipelines developed by the [Group of Chemoinformatics and Drug Design](https://github.com/ci-lab-cz) at the Institute of Molecular and Translational Medicine ([IMTM](https://imtm.cz/)).

---

## Project Links

- **CReM** – https://github.com/DrrDom/crem  
- **EasyDock** – https://github.com/ci-lab-cz/easydock  
- **CReM-dock** – https://github.com/ci-lab-cz/crem-dock  
- **CReM-pharm** – https://github.com/ci-lab-cz/crem-pharm  

---

## Installation

These pipelines are designed to support high-throughput automated docking and structure generation and currently operate exclusively via command-line interfaces (no graphical user interface).

- Commands are executed via the command line on Windows and Linux.
- While the tools can run on Windows, a reduced feature set is available.
- For optimal functionality on Windows, it is recommended to install Windows Subsystem for Linux (WSL2) with Ubuntu and follow the Linux installation instructions.

---

## Windows Installation

1. Install **Git**  
   https://git-scm.com/downloads/win

2. Install **Conda / Miniconda** (if not already installed)  
   https://www.anaconda.com/docs/getting-started/miniconda/install

3. Start the **Anaconda Console** (available from the Start menu)

4. Create the Python environment: `conda env create -f crem_env_win.yml`

5. Install **CDPKit** by downloading the latest release
   https://github.com/molinfo-vienna/CDPKit/releases

6. Update the PATH variable to add the path to binaries of CDPKit
- Press Win + R, type sysdm.cpl, and press Enter.
- Go to Advanced → Environment Variables.
- Under User variables (or System variables if you want it for all users), select Path and click Edit.
- Click New, then paste in your custom path (e.g. `C:\my\custom\path\to\CDPKit\bin`).
- Click OK on all dialogs.

7. Install a binary of **AutoDock Vina**
   https://vina.scripps.edu/downloads/

## Linux/MacOS Installation

1. Install **Conda / Miniconda**
   https://www.anaconda.com/docs/getting-started/miniconda/install
2. Install python environment: `conda env create -f crem_env.yml`
3. Install CDPKit by downloading the latest release
   https://github.com/molinfo-vienna/CDPKit/releases
3.1. (example) `sh CDPKit-1.2.3-Linux-x86_64.sh --prefix=/home/XXX/opt`  
3.2. Set PATH environment variable to include CDPKit binaries; add `CDPKit/Bin` directory to your `$PATH` variable in `.bash_profile`:  
Linux (example)  
`echo ‘PATH=/home/XXX/opt/CDPKit/Bin:$PATH’ >> .bash_profile`  
MacOS (example)  
`echo 'PATH=/home/XXX/opt/CDPKit/Bin:$PATH' >> .zshrc`  

## All platforms
1. Download CReM fragment database compiled from molecules from ChEMBL33 filtered by SA score <= 2 [chembl33_sa2_f5.db.gz](https://zenodo.org/records/16909329/files/chembl33_sa2_f5.db.gz) and extract the database. More databases can be found at https://doi.org/10.5281/zenodo.16909328

## Checking the installations
1. To check that main programs were installed correctly and PATH variable was properly configured you may run the following commands in the console (in the case of success, they will print help messages):  
```
conda activate crem-add9
cremdock -h
crempharm -h

# Linux
confgen –h

# Windows
confgen.exe -h
```

2. Check installation of torch
```
conda activate crem-add9
python -c "import torch"
```
In the case of success, it will print nothing, otherwise an error message will be printed

## Optional installations
These are needed mainly for visualization and analysis of the outputs. Chimera for protein structure preparation. Their installation is not strictly required. However, you may find these tools useful for your work.  
- Chimera (https://www.cgl.ucsf.edu/chimera/download.html)
- PyMOL (https://www.pymol.org/)  
https://pymolwiki.org/index.php/Linux_Install  
https://pymolwiki.org/index.php/MAC_Install  
https://pymolwiki.org/index.php/Windows_Install  
- SQLite browser - https://sqlitebrowser.org/  
- DataWarrior - https://openmolecules.org/datawarrior/download.html  
