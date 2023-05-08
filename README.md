# Jupyter Notebook on Euler SSH Connection and venv Virtual Environment
Jupyter Notebook running in venv on Euler but accessed from local machine.

This guide will help you set up a Jupyter Notebook on the Euler cluster with an SSH connection and a venv virtual environment.

## Final Working Summary

To start a Jupyter Notebook, follow these steps:

1. Run the following command:

```bash
./start_jupyter_nb.sh
````

2. In VSCode, open my_notebook.ipynb, then "Select Kernel" > "Existing Server".

## Setup

To set up the environment, follow these steps:

1. Download the shell script from this [scicomp instructions](https://scicomp.ethz.ch/wiki/Jupyter_on_Euler_and_Leonhard_Open#Running_the_script).
2. Make adjustments for the venv virtual environment. Add and adjust the following lines in the `start_jupyter_nb.sh` file. [(Further Infos)](https://janakiev.com/blog/jupyter-virtual-envs/):

```bash
## start_jupyter_nb.sh

# Configuration file default    : ./.jnb_config
JNB_CONFIG_FILE="./.jnb_config"

...

source "$JNB_VENV_DIR/bin/activate"
pip install --user ipykernel
python -m ipykernel install --user --name=$JNB_VENV_NAME

...

jupyter $JNB_START_OPTION --no-browser --ip "\$JNB_IP_REMOTE" --kernel $JNB_VENV_NAME $JNB_SWORK_DIR &> \$HOME/jnbinfo
````

3. Add the following arguments in the `.jnb_config` file:

```bash
JNB_VENV_DIR="/cluster/project/cvg/students/bmicha/ATISS/atiss_venv" # Path to virtual environment
JNB_VENV_NAME="atiss_venv"                                           # Name of virtual environment
````
