# Installing Miniconda

1. Before doing anything, fetch the latest version of <https://github.com/leelabcnbc/DevOps> to your home directory. I assume that you clone the repo to `~/DevOps`. Unless otherwise indicated, all the scripts below should run without any hacking of environment variables (except those that permanently goes into `.bashrc` as suggested below).
2. Before you can install any Python-based programs, you must first install miniconda.
3. Run `~/DevOps/shell_scripts/conda/install_miniconda.sh INSTALL_PATH` to install miniconda under `INSTALL_PATH` (better be a full path under your home directory), whose default value is `~/miniconda2` if you don't specify it. It must not exist before, otherwise the script will not touch your existing `INSTALL_PATH`
4. After that, you should add a line like `export PATH=${HOME}/miniconda2/bin:$PATH` (depending on `INSTALL_PATH`) into files like `.bashrc` (if you are on CNBC cluster), so that conda related commands are always available (if you don't do this, you have to make sure conda is in `PATH` before running any scripts related to `conda`, or almost all scripts in `DevOps` repo).
