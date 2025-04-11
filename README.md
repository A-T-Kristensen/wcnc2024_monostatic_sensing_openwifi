# wcnc2024_monostatic_sensing_openwifi (Under Construction)

This project builds upon [OpenWiFi](https://github.com/open-sdr/openwifi), an open-source IEEE 802.11/Wi-Fi baseband FPGA design with Linux mac80211-compatible drivers and software, developed by the Open-SDR community. We are not affiliated with the OpenWiFi project or its maintainers; we extend their work for research purposes.

The main extension available in this repo are various scripts to set up the board and ease data collection. We also provide code for post-processing.

## Reference Paper

This work is based on the following publication:

**Monostatic Multi-Target Wi-Fi-Based Breathing Rate Sensing Using OpenWiFi**

Andreas Toftegaard Kristensen, Sitian Li, Alexios Balatsoukas-Stimming, Andreas Peter Burg

*IEEE Wireless Communications and Networking Conference (WCNC) 2024*

[Link to paper](https://ieeexplore.ieee.org/document/10570912)

## Running the Demo

To run the demo, navigate to [experiments/demos/starter](experiments/demos/starter) and follow the README instructions. This will guide you through a basic setup and initial data capture using OpenWiFi-based hardware.

### Pre-requisites

You can download the SD card image from [here](https://drive.google.com/file/d/1uQMX8zfUFNDDfW1cvrgORAVHtUJXXgkP/view?usp=sharing).

Set up a Python environment with the following commands:

```bash
conda config --append channels conda-forge
conda create -n openwifi python=3.9
conda activate openwifi
conda install pandas paramiko pyyaml
```

## Post-Processing the Data

After running the demo and collecting raw CSV data, you can process it using scripts in [scripts_data](scripts_data):

1. Generate a searchable database:

```bash
python script_create_database.py
```

2. Convert CSV files to HDF5 for faster access:

```bash
python script_create_hdf5_files.py
```

HDF5 files load more quickly, especially for large datasets, improving your analysis workflow.

## MATLAB Data Processing

To analyze and visualize the data, open [wispr/script_process_dataset_demo.m](wispr/script_process_dataset_demo.m) in MATLAB. Set the path to your dataset and run the script. This estimates the channel impulse response (CIR) and plots the results.

## Future Work

We are preparing a full release of this project, including FPGA RTL code, Linux kernel modifications, C programs, and Python post-processing tools. This takes time to organize and document properly.

For early access or inquiries, please contact andreas.kristensen@epfl.ch.

Thank you for your patience and support.
