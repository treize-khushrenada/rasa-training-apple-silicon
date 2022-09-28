# Setting up rasa opensource framework on new Mac (Apple Silicon)

Latest update on 28 Sep 2022:

In order to run rasa training process, users need to utilize miniforge channel and mannually install the fundamental rasa packages. Please note that GPUs on M1 cannot be utilized yet.

Below is a step-by-step guide on how to install everything you need on your new Mac:

(credits to [koaning](https://forum.rasa.com/u/koaning), Research Advocate at Rasa)

## 1. Install homebrew and required packages

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

`brew install libpq libxml2 libxmlsec1 pkg-config postgresql`

## 2. Install miniforge and activate base environment

download miniforge here:

https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh

`chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh`

`sh ~/Downloads/Miniforge3-MacOSX-arm64.sh`

`source ~/miniforge3/bin/activate`

## 3. Create conda environment 

example envrironment file (support rasa==2.8.27):

https://github.com/treize-khushrenada/rasa-training-apple-silicon/blob/main/env_rasa2-8.yml

`conda env create -v --name rasa-core-m1 -f env_rasa2-8.yml`

`conda env create -v --name bot-rs-actions-m1 -f env_rasa-actions.yml`

`conda activate rasa-core-m1`

## 4. Add rasa and related packages to the environment

`pip install git+https://github.com/vpol/text.git --no-deps`

`pip install git+https://github.com/RasaHQ/rasa-sdk@2.8.0 --no-deps`

`pip install git+https://github.com/RasaHQ/rasa@2.8.27 --no-deps`

if spacy package is needed for your training pipeline:

`conda install spacy==3.2.2`

## More information about on-going issues/ progress:

https://forum.rasa.com/t/an-unofficial-guide-to-installing-rasa-on-an-m1-macbook/51342

https://forum.rasa.com/t/module-tensorflow-python-keras-engine-training-has-no-attribute-enable-multi-worker/41502/