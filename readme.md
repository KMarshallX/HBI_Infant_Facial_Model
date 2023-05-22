# HBI3 Premature Infant Face Reconstruction
## **Declaration**
This repo is only for BIOE6901 HBI3 team to store, manage backend project 
## **Installation**
_**IMPORTANT**_ Please make sure execute the software in Unix environment with NVidia GPU and CUDA installed. 
1. Environment setup

```
# Clone the code locally and install required softwares
git clone https://github.com/KMarshallX/HBI_Infant_Facial_Model.git
cd HBI_Infant_Facial_Model
conda env create -f environment.yml
source activate hbi_infant

# Install Nvdiffrast library
cd nvdiffrast
pip install .
cd .. 
```

2. Load face model expressor\
Download [BFM09](https://drive.google.com/file/d/1Dz7fEenOYBPYe0Mp3wPLsC12wiSDK6Xk/view?usp=share_link) and [Expression Basis](https://drive.google.com/file/d/1d0f0m6MsDVNmCSyAmM1V5pIhi49_1Ozr/view?usp=share_link) and put the files under BFM directory
```bash
HBI_Infant_Facial_Model
│
└─── BFM
    │
    └─── 01_MorphableModel.mat
    │
    └─── Exp_Pca.bin
    |
    └─── ...
```

3. Load pre-trained weights
Download a pretrained model from [this link](https://drive.google.com/file/d/1z2YeR5SvYv9L0yXcQb9Lg0llXP2Eb9gZ/view?usp=sharing) and put the pretrained weights in the following structure
```bash
HBI_Infant_Facial_Model
│
└─── checkpoints
    │
    └─── <model_name>
        │
        └─── epoch_20.pth
```
## **Make inference**
Put the images you are going to reconstruct facial model from under the root directory:
```bash
Deep3DFaceRecon_pytorch
│
└─── <folder_to_test_images>
    │
    └─── *.jpg/*.png
```
Run the script:
```
python test.py --name=<model_name> --epoch=20 --img_folder=<folder_to_test_images>
```
The results will be saved into ./checkpoints/<model_name>/results/<folder_to_test_images>