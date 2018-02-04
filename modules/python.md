# Install python and related packages

## default environment

`~/DevOps/shell_scripts/conda/envs/default.sh NAME` and `~/DevOps/shell_scripts/conda/envs/default-3.sh NAME` are two scripts to install 'default' Python 2/3 environments. If `NAME` is not specified, then `NAME` is `default` for `default.sh` and `default-3` for `default-3.sh`.  Currently, by default, I mean the following set of packages from conda-forge (plus Python 2 or 3, of course):

    ~~~
    numpy
    scipy
    matplotlib
    pandas
    nose
    notebook
    h5py
    openblas
    git
    ~~~
    
    These packages form the very basics for doing research in Python. They are needed for probably every project. Yimeng has made sure that these packages are up-to-date and (most of them) are not broken. Here, broken means that a package can't pass its own testing suite. Yimeng has set up a mechanism for automatically testing `numpy`, `scipy`, `pandas`, and `h5py`. See <https://travis-ci.org/leelabcnbc/DevOps>.


## additional packages
    
There are some other packages that should be very useful. For each of them (named `X`), you should best install them with syntax `conda install -c conda-forge --no-update-dependencies X` to minimize your troubles (this is the opinion of Yimeng).
	
	~~~
	scikit-learn
	joblib
	scikit-image
	~~~
