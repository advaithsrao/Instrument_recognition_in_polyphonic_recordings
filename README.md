

## Overview

This repository contains an implementation of multiinstrument detection in polyphonic recordings on the OpenMIC-2018 dataset.

## Reference

>Humphrey, Eric J., Durand, Simon, and McFee, Brian. "OpenMIC-2018: An Open Dataset for Multiple Instrument Recognition." in Proceedings of the 19th International Society for Music Information Retrieval Conference (ISMIR), 2018. [pdf](https://zenodo.org/record/1492445#.XsPDCRMzZTY)


## Instructions to run
### Install docker
https://docs.docker.com/engine/install/

### Clone the repo locally

```bash
cd /some/dir
git clone https://github.com/advaithsrao/multiinstrument_recognition_in_recordings.git
```

### Pull tensorflow-1.15-gpu image from **https://hub.docker.com/r/tensorflow/tensorflow/tags?page=8&ordering=last_updated**

```bash
docker pull tensorflow/tensorflow:1.15.4-gpu-py3-jupyter
```

### Get the IMAGE_ID corresponding to *REPOSITORY* tensorflow/tensorflow
```bash
docker images
```

Copy this IMAGE_ID

### Spin up the container
```bash
docker run -it -p 8888:8888  -v multiinstrument_recognition_in_recordings:/tf <IMAGE_ID>
```

*Please open jupyter notebook throgh the link echoed on the CLI*

### VGGish model init
you'll want to pull down the VGGish model parameters via the following script.

**Since we opened the docker image interactively and not through /bin/bash , let us open terminal on the 'jupyter home' itself**
`Click New -> Terminal; and enter the command`

```bash
./scripts/download-deps.sh
```

### Download the dataset required for the implementation, The OpenMIC-2018 dataset is made [available on Zenodo](https://zenodo.org/record/1432913#.W6dPeJNKjOR). 

Decompress the contents to `./data/` in the local repository.

#### We shall use 

1. (`./data/<downloaded_dataset>/openmic-2018.npz`) -> Contains the required training and testing data with ['X', 'Y_true', 'Y_mask', 'sample_key']
2. (`./data/<downloaded_dataset/audio/>`) -> OGG Vorbis files to test the model

### Now open main.py and run all cells
