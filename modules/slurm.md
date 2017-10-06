# Using slurm

1. 'srun -N1 --cpus-per-task=24 --gres=gpu:4 --mem=0 --time=4-0:00:00 --pty bash' to request a job.
2. 'squeue' to see a list of the current jobs
3. 'scancel jobID' to cancel a job

4. visit https://slurm.schedmd.com for more details.
