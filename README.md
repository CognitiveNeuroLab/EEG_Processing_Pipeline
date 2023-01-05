# EEG_Processing_Pipeline
A pipeline to clean and epoch EEG data collected using a Biosemi ActiveTwo EEG system. This pipeline is designed to process 64 channel, 128 channel, and 160 channel data.

## Requirements
1. MATLAB
2. EEGLab Toolbox
  - Download from here: https://sccn.ucsd.edu/eeglab/download.php

## Processing Steps Performed

1. Initialize / load data
2. Resample
   - Optional step
4. Remove externall channels
5. Get channel locations
6. Line noise removal
7. Filtering (high and low pass)
8. Re-reference to common average
9. ICA
   - Optional step
10. Epoch
11. Baseline
12. Trial Rejection
13. Generate plots for quality control and manual inspection
14. Finalize
15. Save data
16. Generate log file

## Input Folder Structure and Filenaming Conventions

- My_Data **[Parent Directory]**
  - 1001 **[Subject ID]**
    - 1001_1.bdf [BDF file]
    - 1001_2.bdf [BDF file]
    - 1001_3.bdf [BDF file]
  - 1002 **[Subject ID]**
    - 1002_1.bdf [BDF file]
    - 1002_2.bdf [BDF file]
    - 1002_3.bdf [BDF file]
    - 1002_4.bdf [BDF file]
  - 1003 **[Subject ID]**
    - 1003_1.bdf [BDF file]

### Notes

- Subject-level folder names must include only digits
  - **Valid folder name**: 12345
  - **Invalid folder name**: Sub12345
- BDF files will be concatenated in alphebetical order into a single .mat file
- Each subject is allowed to have a different number of BDF files (minimum of 1)

## Technical Information
This pipeline was coded in MATLAB (R2021b) on a PC platform running Windows 10 . The pipeline was also tested for Mac compatibility in MATLAB (R2022b) on a Mac Mini running Monterey (v 12.5.1)

## Acknowledgements

Inspired by pipelines by @mickcrosse and @DouweHorsthuis!
