# quarto_template_multilang
Multilanguage Quarto Template

# Start GPU node interactively
`srun --ntasks=1 --cpus-per-task=1 --partition=vis --gres=gpu:1 --time=12:00:00 --mem=200G --x11 --pty bash`

# Setup
## Retrieve and start singularity container
### Retrieve pre-made singularity container from dockerhub
`ml Singularity/3.6.4`

`singularity shell --bind  /nemo:/nemo,/camp:/camp /nemo/lab/rouhanif/home/users/boeings/singularity_images/r450.python310.ubuntu.22.04.singularity.image/r450.python310.ubuntu.22.04.V2.sif`
`singularity shell --bind  /nemo:/nemo,/camp:/camp /nemo/lab/rouhanif/home/users/boeings/singularity_images/r450.python310.ubuntu.22.04.singularity.image/r450.python310.ubuntu.22.04.V2.sif`

### Start GPU node interactively

### Use on a GPU node
`singularity shell --nv --bind  /nemo:/nemo,/camp:/camp /nemo/lab/rouhanif/home/users/boeings/singularity_images/r450.python310.ubuntu.22.04.singularity.image/r450.python310.ubuntu.22.04.V2.sif`


## Setup python-venv package environment
### Or create venv environment in the current folder (change path if you'd like to store the venv environment files elsewhere)
python3.10 -m venv single_cell_venv_310

### Activate venv environment
`source single_cell_venv_310/bin/activate`

## Setup R-renv package environment
### Specifying R-library paths
`export RENV_PATHS_LIBRARY=/nemo/lab/rouhanif/home/users/boeings/R/library`
`export RENV_PATHS_CACHE=/nemo/lab/rouhanif/home/users/boeings/R/cache`

### Configuring analysis modules to run and initiation of workflow
Open the '_quarto.yml' file in a text editor, and comment out all modules you don't want to run. Then save and close the '_quarto.yml' file.

Start the workflow - as specified by the _quarto.yml file - by running after starting R:

`quarto::quarto_render()`
