# Opening interactive jupyter notebook

Start a job using **srun -N1 --cpus-per-task=24 --gres=gpu:4 --mem=0 --time=4-0:00:00 --pty bash**
Use **tmux** to create a new sessions
Press **CTRL + b c** to create more session
Toggle between the sessions by pressing **CTRL + b session no.**
close a session by pressing **CTRL + b x**
In session 0 **~/DevOps/connection_scripts/slurm_create_one_port_mapping.sh** for Ssh mapping from compute node to head node[compute node]
Go to your local terminal (on your laptop) **ssh -N -L 8899:localhost:8899 xingyul2@psych-o.hpc1.cs.cmu.edu** for Ssh mapping from local server
Go into session 1 active environment and **jupyter notebook --no-browser --port=8899** to open a jupyter notebook on the server
Open **http://localhost:8894** on local browser to use the jupyter notebook on your local computer