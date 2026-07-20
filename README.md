# Repository Structure and Data Directory Hierarchy

This repository is organized into four primary directories designed to facilitate the processing, simulation, and visualization of Ion Beam Analysis (IBA) data (PIXE/EBS) for deep-sea geological specimens.

---

## Repository Overview

```text
.
├── 1_Raw_DATA/            # Raw data, spectra (.SPO/.ODF), maps & R33 cross-sections
├── 2_Simulated_DATA/      # Simulation files (GUPIXWIN & WINDF)
├── 3_Python_Files/        # Jupyter Notebooks (.ipynb) for data visualization & processing
└── 4_Filtered_DATA/       # Folders with summary Excels & Run-indexed vector plots
```

---

## 1. Raw_DATA

The `Raw_DATA` directory contains all unaltered primary outputs generated directly from the experimental equipment, initial pre-processing routines, and foundational nuclear reaction cross-section data, partitioned into `2_MeV` and `700_keV` energy configurations:

* **`Accelerator_Raw_Files/`**: Archives foundational metadata, logbooks, and operational parameters from the electrostatic accelerator platform.
* **`Spectra_Files/`**: Houses target-ready experimental spectra files:
  * **`.SPO` files**: Optimized for PIXE elemental fitting in **GUPIXWIN**.
  * **`.ODF` files**: Optimized for EBS spectral fitting in **WINDF**.
* **`R33_Files/`**: Contains evaluated experimental and theoretical differential cross-section data files in standard **.R33 format** retrieved from the IAEA Ion Beam Analysis Data Library (**IBANDL**). These files (e.g., SigmaCalc evaluated cross-sections like $^{12}\text{C}(p,p_0)^{12}\text{C}$) supply non-Rutherford Elastic Backscattering Spectrometry (EBS) simulation engines (such as **WINDF**) with accurate energy-dependent, angular differential cross-sections ($\text{mb/sr}$) and resonance structures required for precise light-element quantification.
* **`Maps/`**: Stores 2D spatial distribution data, including raw list-mode acquisition files (`.LMF`), exported numerical intensity matrices (`.csv`), vector maps (`.pdf`), and the automated batch-mapping notebook (`iba_batch_mapping.ipynb`).

---

## 2. Simulated_DATA

Archives all simulation inputs, boundary conditions, and execution outputs used to model and quantify experimental spectra:

* **`PIXE_Spectra/`**: Subdivided by run number. Contains raw spectra, **GUPIXWIN** configuration parameter files (`.PAR`), derivative numerical outputs, and compiled spectrum fit plots (`.pdf`).
* **`EBS_Spectra/`**: Subdivided by run number. Contains foundational **WINDF** input arrays alongside derivative simulation outputs.
  
  *Note on Cross-Methodology Calibration:* Includes `calpixe.eff` and `pixe_h.geo` calibration files, which embed PIXE-derived concentration constraints into the EBS simulation framework for self-consistent dual-target evaluation.

---

## 3. Python_Files

Serves as the central repository for all Interactive Jupyter Notebooks (`.ipynb`) dedicated to data visualization and processing. These notebooks automate data parsing, matrix manipulation, statistical analysis, and the rendering of figures, spectra fits, and spatial maps.

---

## 4. Filtered_DATA

The final refined output repository organized by target matrix type into three primary subdirectories: `Foraminifera/`, `Lucky_Strike/`, and `Polymetallic_Nodules/`.

### Directory Organization & Data Products
* **Matrix Root Level:** Each matrix category folder contains the master concentration database provided in two identical formats for accessibility:
  * **Master Concentration Table (`.xlsx` & `.png`)**: A consolidated table detailing elemental concentrations and associated experimental uncertainties across all target runs, provided as an editable Excel sheet (`.xlsx`) alongside an equivalent image (`.png`) for quick visual reference.
* **Run-Specific Subdirectories:** Subdivided into individual experimental run numbers, each containing high-resolution vector plots (`.pdf`):
  1. Fitted **PIXE spectrum** layout.
  2. Fitted **EBS spectrum** layout.
  3. **PIXE vs. EBS concentration comparison** plot.
  4. **Depth distribution profiles** (specifically featured within `Foraminifera/` run folders to characterize stratigraphically non-homogeneous layers).

---

## Licensing

The contents of this repository are dual-licensed as follows:

* **Software & Scripts (`Python_Files/` and code scripts):** Distributed under the **MIT License**. See the [`LICENSE`](./LICENSE) file for full details.
* **Data, Spectra, Maps & Documentation (`Raw_DATA/`, `Simulated_DATA/`, `Filtered_DATA/`):** Covered under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)**.