# EEG_Processing_Pipeline
A pipeline to clean and epoch EEG data collected using a Biosemi ActiveTwo EEG system. This pipeline is designed to process 64 channel, 128 channel, and 160 channel data.

## Requirements
1. MATLAB
2. EEGLab Toolbox
  - Download from here: https://sccn.ucsd.edu/eeglab/download.php

## Before running this code, edit these lines

1. RUNME.m

```
addpath(genpath('PATH/TO/CODE/DIRECTORY'));
dirpath.ParentDir='PATH/TO/DATA/DIR'; 
FolderEnding='_OPTIONAL_DESCRIPTION_OF_ANALYSIS'; 
dirpath.EEGLabDir='PATH/TO/EEGLAB'; 
```

**PATH/TO/CODE/DIRECTORY**: The full path to the unzipped .zip file downloaded from this repository

  - Example for Mac: '/Users/me/Desktop/Preprocessing_Code'
  - Example for PC: 'C:\Users\me\Desktop\Preprocessing_Code'
  - 
**PATH/TO/DATA/DIR**: The full path to the parent directory containing your subject-level folders
  - Example for Mac: '/Users/me/Desktop/My_Data'
  - Example for PC: 'C:\Users\me\Desktop\My_Data'
**OPTIONAL_DESCRIPTION_OF_ANALYSIS**: An optional string to be appended to the end of your folder names. This can be helpful for organizing different analyses. Please include an underscore in the optional string. May be left blank
  - Example: '_Stimulus_Locked_Analysis'
  - Example 2: '_HighPassFilter2Hz'
  - Example 3: '_Processed_By_Jane_Doe'
  - Example 4: '' 
**PATH/TO/EEGLAB**: The full path to where EEGLab is installed
  - Example for Mac: '/Users/me/Documents/MATLAB/eeglab2022.1'
  - Example for PC: 

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

## Folder Structure

### Input 
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

### Output

- My_Data **[Parent Directory]**
  - 1001 **[Subject ID]**
    - 1001_bdf
      - 1001_1.bdf [BDF file]
      - 1001_2.bdf [BDF file]
      - 1001_3.bdf [BDF file]
    - 1001_mat
      - 1001.mat [MAT file]
      - 1001.set [SET file]
    - 1001_mat_OptionalString
    - 1001_erps_OptionalString
    - 1001_plots

### Notes

- Subject-level folder names must include only digits
  - **Valid folder name**: 12345
  - **Invalid folder name**: Sub12345
- BDF files will be concatenated in alphebetical order into a single .mat file
- Each subject is allowed to have a different number of BDF files (minimum of 1)

## Technical Information
This pipeline was coded in MATLAB (R2021b) on a PC platform running Windows 10 . The pipeline was also tested for Mac compatibility in MATLAB (R2022b) on a Mac Mini running Monterey (v 12.5.1). This pipeline has not been tested on Linux.

## Acknowledgements

Inspired by pipelines by @mickcrosse and @DouweHorsthuis!
