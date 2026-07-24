---
layout: post
title: "Getting started with AllenSDK and Neurodata Without Borders"
date: 2024-09-25
tags: [Neuroscience, Tutorial]
excerpt: "How to set up AllenSDK to download Allen Institute electrophysiology data in the Neurodata Without Borders (NWB) format."
---

The AllenSDK (Allen Software Development Kit) is a Python package that facilitates downloading and manipulating Allen Institute data sets. Using the AllenSDK, Allen Brain Observatory experimental data can be retrieved in the Neurodata Without Borders (NWB) file format.

NWB is a data standard for neurophysiology, providing neuroscientists with a common standard to share, archive, use, and build analysis tools for neurophysiology data. It is designed to store a variety of neurophysiology data, including intracellular and extracellular electrophysiology experiments, optical physiology experiments, and tracking and stimulus data.

## Installation guide

To get started with this resource, we need to set up our Python environment and install the required package. Here are the steps:

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

### Example notebooks

I have shared some example notebooks in [this GitHub repository](https://github.com/JesusGF1/neurodataWB) that demonstrate how to work with the AllenSDK and NWB files.

### Additional resources

For more information, check out these useful links:

- [Neurodata Without Borders official website](https://www.nwb.org/)
- [SpikeInterface documentation](https://spikeinterface.readthedocs.io/en/latest/)
- [AllenSDK Visual Coding Neuropixels documentation](https://allensdk.readthedocs.io/en/latest/visual_coding_neuropixels.html)
