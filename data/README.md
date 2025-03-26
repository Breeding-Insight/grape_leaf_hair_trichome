Grape Blackbird

This repository contains code for analyzing grape phenotyping data collected using the Blackbird imaging system. All data, models, and configurations are stored on the Cornell BioHPC server.
Repository Structure

The project on csubi2 is organized as follows:
Text Only

workdir/data/grape/grape_pheno/grape_blackbird/
├── configs/                 # Configuration files
│   └── pytorch_nighlty-env.yaml   # Conda environment configuration
│
├── data/                    # Data storage
│   ├── annotations/         # Annotation files for training models
│   ├── processed/           # Processed data files
│   └── **raw/                 # Raw data files
│       └── blackbird_images/# Original blackbird images
│           └── 001-GBC28_R1_P7_S1.png # Example image file
│           └── [additional image files]**
│
├── models/                  # Trained models
│   └── phenotyping/         # Phenotyping model files
│       └── checkpoints_*/   # Model checkpoints from various training runs
│           └── final_checkpoint.pth # Most up to date checkpoint
│
└── scripts/                 # Analysis and utility scripts

Data Storage

All data for this project is stored on the Cornell BioHPC server and is not included in the GitHub repository. The data is located at:
Text Only

/workdir/data/grape/grape_pheno/grape_blackbird/

Data Access

To access the data, you need an account on the Cornell BioHPC server. There are several methods to access the data:
1. Direct Server Access
Bash

# SSH into the server
ssh username@cbsubi2.biohpc.cornell.edu

# Navigate to the project directory
cd /workdir/data/grape/grape_pheno/grape_blackbird/

2. SSHFS Mount

You can mount the remote directory to your local machine:
Bash

# Create a mount point
mkdir -p ~/server_mounts/grape_blackbird

# Mount the remote directory
sshfs username@cbsubi2.biohpc.cornell.edu:/workdir/data/grape/grape_pheno/grape_blackbird ~/server_mounts/grape_blackbird

3. SFTP Access

For transferring files:
Bash

sftp username@cbsubi2.biohpc.cornell.edu:/workdir/data/grape/grape_pheno/grape_blackbird

Data Organization
Raw Data

The raw data consists of Blackbird imaging system output stored in:
Text Only

/workdir/data/grape/grape_pheno/grape_blackbird/raw/blackbird_images/

Image Naming Convention

Images follow the naming convention:
Text Only

[sequence]-[genotype]_[replicate]_[plant]_[session].png

Example: 001-GBC28_R1_P7_S1.png

    001: Sequence number
    GBC28: Genotype identifier
    R1: Replicate 1
    P7: Plant 7
    S1: Session 1

Models

Trained models are stored in the models directory:
Text Only

/workdir/data/grape/grape_pheno/grape_blackbird/models/

Each checkpoint directory contains model weights and training logs.
Environment Setup

To set up the required environment, use the provided conda environment file:
Bash

# SSH into the server
ssh username@cbsubi2.biohpc.cornell.edu

# Navigate to the project directory
cd /workdir/data/grape/grape_pheno/grape_blackbird/

# Create conda environment
conda env create -f configs/blackbird-env.yaml

# Activate the environment
conda activate grape-blackbird

Running the Code

To run the code in this repository, you'll need to:

    Clone this GitHub repository
    Access the data on the Cornell BioHPC server
    Update the data paths in the configuration files to point to your data location

Example:
Bash

# Clone the repository
git clone https://github.com/username/grape-blackbird.git
cd grape-blackbird

# Set up data paths
export DATA_ROOT=/path/to/mounted/data
# OR
export DATA_ROOT=/workdir/data/grape/grape_pheno/grape_blackbird/

# Run a script
python scripts/analyze_images.py --config configs/analysis_config.yaml

Model Checkpoints

The model checkpoints are organized by timestamp in the format checkpoints_YYYYMMDD_HHMMSS. Each checkpoint directory contains:

    Model weights (.pth files)
    Training configuration
    Training and validation logs
    Evaluation metrics

Contributing

When contributing to this repository, please note that the data should remain on the server and not be committed to GitHub. Update paths in your code to reference the server location.
Contact

For questions about this project or access to the data, please contact the project maintainers.

Note: This README provides an overview of the project structure and data organization. For detailed usage instructions, please refer to the documentation in the specific script files.
