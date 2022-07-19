# PyTracking
A general python framework for visual object tracking and video object segmentation, based on **PyTorch**.

### One tracking paper accepted at CVPR 2022!
* [Transforming Model Prediction for Tracking](https://arxiv.org/abs/2203.11192) | **Code available!**

### Two tracking/VOS papers accepted at ICCV 2021!
* [Learning Target Candidate Association to Keep Track of What Not to Track](https://arxiv.org/abs/2103.16556) | **Code available!**  
* [Generating Masks from Boxes by Mining Spatio-Temporal Consistencies in Videos](https://arxiv.org/abs/2101.02196) | Code coming here soon...  


## Highlights

### KeepTrack and DiMP Trackers

Official implementation of the **KeepTrack** (ICCV 2021), **DiMP** (ICCV 2019), including complete **training code** and trained models.

### [Tracking Libraries](pytracking)

Libraries for implementing and evaluating visual trackers. It includes

* All common **tracking** and **video object segmentation** datasets.  
* Scripts to **analyse** tracker performance and obtain standard performance scores.
* General building blocks, including **deep networks**, **optimization**, **feature extraction** and utilities for **correlation filter** tracking.  

### [Training Framework: LTR](ltr)
 
**LTR** (Learning Tracking Representations) is a general framework for training your visual tracking networks. It is equipped with

* All common **training datasets** for visual object tracking and segmentation.  
* Functions for data **sampling**, **processing** etc.  
* Network **modules** for visual tracking.
* And much more...


### [Model Zoo](MODEL_ZOO.md)
The tracker models trained using PyTracking, along with their results on standard tracking 
benchmarks are provided in the [model zoo](MODEL_ZOO.md). 


## Trackers
The toolkit contains the implementation of the following trackers.

### KeepTrack (ICCV 2021)

**[[Paper]](https://arxiv.org/abs/2103.16556)  [[Raw results]](MODEL_ZOO.md#Raw-Results-1)
  [[Models]](MODEL_ZOO.md#Models-1)  [[Training Code]](./ltr/README.md#KeepTrack)  [[Tracker Code]](./pytracking/README.md#KeepTrack)**

Official implementation of **KeepTrack**. KeepTrack actively handles distractor objects to
continue tracking the target. It employs a learned target candidate association network, that
allows to propagate the identities of all target candidates from frame-to-frame.
To tackle the problem of lacking groundtruth correspondences between distractor objects in visual tracking,
it uses a training strategy that combines partial annotations with self-supervision. 

![KeepTrack_teaser_figure](pytracking/.figs/KeepTrack_teaser.png)


### DiMP (ICCV 2019)
**[[Paper]](https://arxiv.org/pdf/1904.07220)  [[Raw results]](MODEL_ZOO.md#Raw-Results)
  [[Models]](MODEL_ZOO.md#Models)  [[Training Code]](./ltr/README.md#DiMP)  [[Tracker Code]](./pytracking/README.md#DiMP)**
    
Official implementation of the **DiMP** tracker. DiMP is an end-to-end tracking architecture, capable
of fully exploiting both target and background appearance
information for target model prediction. It is based on a target model prediction network, which is derived from a discriminative
learning loss by applying an iterative optimization procedure. The model prediction network employs a steepest descent 
based methodology that computes an optimal step length in each iteration to provide fast convergence. The model predictor also
includes an initializer network that efficiently provides an initial estimate of the model weights.  

![DiMP overview figure](pytracking/.figs/dimp_overview.png)

## Installation

#### Clone the GIT repository.  
```bash
git clone https://github.com/visionml/pytracking.git
```
   
#### Clone the submodules.  
In the repository directory, run the commands:  
```bash
git submodule update --init  
```  
#### Install dependencies
Run the installation script to install all the dependencies. You need to provide the conda install path (e.g. ~/anaconda3) and the name for the created conda environment (here ```pytracking```).  
```bash
bash install.sh conda_install_path pytracking
```  
This script will also download the default networks and set-up the environment.  

**Note:** The install script has been tested on an Ubuntu 18.04 system. In case of issues, check the [detailed installation instructions](INSTALL.md). 

**Windows:** (NOT Recommended!) Check [these installation instructions](INSTALL_win.md). 

#### Let's test it!
Activate the conda environment and run the script pytracking/run_webcam.py to run ATOM using the webcam input.  
```bash
conda activate pytracking
cd pytracking
python run_webcam.py keep_track default    
```  


## What's next?

#### [pytracking](pytracking) - for implementing your tracker

#### [ltr](ltr) - for training your tracker

