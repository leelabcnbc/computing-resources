# Install python and related packages

1. ~/DevOps/shell_scripts/conda/envs/default.sh and ~/DevOps/shell_scripts/conda/envs/default-3.sh are two scripts to install a 'default' Python 2/3 environment, respectively. Currently, by default, I mean the following set of packages from conda-forge (plus Python 2 or 3, of course):

    numpy
    scipy
    matplotlib
    pandas
    nose
    notebook
    h5py
    openblas
    git # yes because the old git on cluster doesn't support my .gitignore files.
