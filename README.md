# Ata Berk Öztürk

Physics engineer (Ankara University, 2026) working on computational materials science. Most of my work is density functional theory for two-dimensional materials with VASP and Quantum ESPRESSO, run on Slurm clusters, plus the Python around it: input generation, output parsing, data analysis and some machine learning. I started an M.Sc. in Physics Engineering at Ankara University in 2026 and I am looking for a research / R&D position in computational materials, HPC or scientific software.

Website: [ataberkozturk.com](https://ataberkozturk.com) · LinkedIn: [ata-berk-ozturk](https://www.linkedin.com/in/ata-berk-ozturk)

## Research

**Computational Condensed Matter Physics group, Ankara University** (2024 – present, [hymf.ankara.edu.tr](https://hymf.ankara.edu.tr)). Band structures, densities of states and magnetic moments of 2D materials with VASP; surface adsorption studies run as batch jobs on the group's Slurm cluster (VASP 5.4.1, Intel MPI). Inputs, job submission and output parsing are scripted in Bash and Python.

**TÜBİTAK 2209-A undergraduate research grant** (2025 – 2026). Surface functionalisation of the Janus monolayers SnSSe and TiSSe studied with DFT: adsorption sites, structural relaxation, phonons and optical properties. Presented as a poster at the 29th Condensed Matter Physics Ankara Meeting (Hacettepe University, December 2024) and at the Ankara University 80th Anniversary Student Projects Congress (June 2026).

**B.Sc. thesis: machine learning for magnetic 2D materials** (2025 – 2026). A gradient boosting classifier that predicts the magnetic label of 2D materials from chemical composition, trained on the C2DB and V2DB databases. Received a poster award at the department's thesis presentations (January 2026). The code, and a later revision with stricter validation, is in [2d-magnetic-materials-ml](https://github.com/eigen-ml/2d-magnetic-materials-ml).

## Projects

### [2d-magnetic-materials-ml](https://github.com/eigen-ml/2d-magnetic-materials-ml)

My thesis project, revised after the thesis. The current version trains on 127,024 V2DB compositions, picks the decision threshold on a separate validation split and reports three kinds of validation: a held-out test split, cross-validation grouped by chemical system, and leave-one-element-out. The last one is the useful result: the model ranks compositions well inside known chemistry (ROC-AUC 0.999) but misses most magnetic compounds when an element such as Mn or Cr was never seen in training (recall 1–33%). The README has the tables and figures. The model is also served through a small FastAPI service with a Dockerfile, and CI builds the image and calls the API.

Python · scikit-learn · pymatgen · FastAPI · Docker · GitHub Actions

<img src="https://raw.githubusercontent.com/eigen-ml/2d-magnetic-materials-ml/main/figures/eval_leave_element_out.png" width="560" alt="ROC-AUC and recall when one element is left out of training">


### [dft-hpc-toolkit](https://github.com/eigen-ml/dft-hpc-toolkit)

Tools I use around DFT runs on clusters, collected into one package without dependencies so it runs on login nodes:

- Slurm templates for VASP, pw.x and job arrays
- `dfthpc scan` / `summary`: cutoff and k-point convergence tests, with the energy difference per atom against the densest setting
- `dfthpc parse`: OUTCAR and pw.x output parsers (energies, SCF and relaxation status, Fermi level, magnetization, timing), checked against 109 of my own VASP runs and the Quantum ESPRESSO test-suite outputs
- `dfthpc watch`: SCF history of a running job, marking ionic steps that hit the iteration limit
- an AUSURF112 scaling benchmark (1–8 MPI ranks, 87% parallel efficiency on 8 ranks)
- notes on building Quantum ESPRESSO, setting up single-node Slurm and using Docker / Apptainer on Rocky Linux 8

Python · Bash · Slurm · VASP · Quantum ESPRESSO · pytest · shellcheck

<img src="https://raw.githubusercontent.com/eigen-ml/dft-hpc-toolkit/main/benchmarks/ausurf112/scaling.png" width="560" alt="AUSURF112 speedup and parallel efficiency on 1 to 8 MPI ranks">


### [fish-length-estimation](https://github.com/eigen-ml/fish-length-estimation) (work in progress)

Estimating fish length and weight from camera images for aquaculture: a YOLO detector, length measurement from segmentation masks along the principal axis, a scale from a reference object and the length–weight relation W = aL^b. The measurement code is tested on synthetic shapes; the detector is so far trained only on a public reef-fish dataset. Calibration against measured and weighed trout is the next step.

Python · OpenCV · Ultralytics YOLO

<img src="https://raw.githubusercontent.com/eigen-ml/fish-length-estimation/main/docs/img/predictions.jpg" width="560" alt="Detector output on test images">


## HPC experience

**HPC intern, EDULINE, Istanbul** (July – August 2025). Built Quantum ESPRESSO 7.4.1 from source on Rocky Linux 8.10 (Open MPI, OpenBLAS, FFTW, ScaLAPACK) and traced a parallel "Illegal instruction" failure to missing AVX support in the virtual CPU. Ran the AUSURF112 benchmark on 1–8 cores and compared it with published results. Set up a single-node Slurm system with munge from the OpenHPC repositories, and worked with Docker and Apptainer for running QE in containers. Wrote the installation documentation for the company; cleaned-up versions are in dft-hpc-toolkit.

**ARCHER2 HPC Driving Test** (University of Edinburgh, 2025).

## Education

- M.Sc. Physics Engineering, Ankara University (2026 – present), advisor Prof. Dr. Yeşim Moğulkoç
- B.Sc. Physics Engineering, Ankara University (2022 – 2026), taught in English

## Tools

VASP, Quantum ESPRESSO, VESTA · Python (NumPy, pandas, scikit-learn, pymatgen, matplotlib) · Bash · Slurm, OpenHPC, Open MPI · Docker, Apptainer · Linux (Rocky, Ubuntu) · Git, GitHub Actions · C++, Fortran
