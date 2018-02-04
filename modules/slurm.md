# Using slurm

1. run something like `srun -N1 --cpus-per-task=24 --gres=gpu:4 --mem=0 --time=4-0:00:00 --pty bash` to request a job. below is something you can change
    * `--cpus-per-task=24` number of cpus to request. For `compute-1-1/3/5`, max is 24, for `compute-1-7/9/11`, max is 32. Not sure about `compute-1-13`.
    * `--gres=gpu:4` request `X` (`X=4` here) GPUs. If not needed, don't include it.
    * `--mem=0` memory requested. `0` means all memory. You can do other things like `--mem=2000m` or `--mem=10G`, etc. For running Caffe or programs that can eat all memory, you should use `--mem=0`. Otherwise, your program will get killed.
    * `--time=4-0:00:00` gives how long you want to run session. `4-0:00:00` means four days, `12:00:00` means 12 hours, etc.
2. `squeue` to see a list of the current jobs
3. `scancel jobID` to cancel a job. `scancel -u XXX` to cancel all jobs by user `XXX`.
4. visit <https://slurm.schedmd.com> and <https://www.rc.fas.harvard.edu/resources/documentation/convenient-slurm-commands/> for more details.
