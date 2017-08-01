# Using slurm

**srun -N1 --cpus-per-task=24 --gres=gpu:4 --mem=0 --time=4-0:00:00 --pty bash** to request a job.
**squeue** to see a list of the current jobs
**scancel jobID** to cancel a job

visit https://slurm.schedmd.com for more details.