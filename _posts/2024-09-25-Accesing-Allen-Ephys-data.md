# Getting Started with AllenSDK and Neurodata Without Borders

## Introduction

The AllenSDK (Allen Software Development Kit) is a Python package that facilitates downloading and manipulating Allen Institute data sets. Using the AllenSDK, Allen Brain Observatory experimental data can be retrieved in the Neurodata Without Borders (NWB) file format. 

NWB is a data standard for neurophysiology, providing neuroscientists with a common standard to share, archive, use, and build analysis tools for neurophysiology data. NWB is designed to store a variety of neurophysiology data, including data from intracellular and extracellular electrophysiology experiments, data from optical physiology experiments, and tracking and stimulus data.

## Installation Guide

To get started using this resource, we need to set up our Python environment and install the required package. Here are the steps:

```bash
# Create a new conda environment with Python 3.8
conda create -n allensdk python=3.8

# Initialize conda for your shell
conda init

# Activate the new environment
conda activate allensdk

# Install the AllenSDK package
pip install allensdk
```

## Resources

### Example Notebooks
I've shared some example notebooks in [this GitHub repository](https://github.com/JesusGF1/neurodataWB) that demonstrate how to work with the AllenSDK and NWB files.

### Additional Resources
For more information, check out these useful links:

* [Neurodata Without Borders Official Website](https://www.nwb.org/)
* [SpikeInterface Documentation](https://spikeinterface.readthedocs.io/en/latest/)
* [AllenSDK Visual Coding Neuropixels Documentation](https://allensdk.readthedocs.io/en/latest/visual_coding_neuropixels.html)