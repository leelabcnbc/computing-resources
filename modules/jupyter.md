# Opening interactive jupyter notebook

As of 20170801, this works with the GPU nodes of the CNBC cluster. Similar methods should work for CPU nodes as well.

1. Get an interactive session on a compute node with `srun`, such as `srun -N1 --cpus-per-task=24 --gres=gpu:4 --mem=0 --time=4-0:00:00 --pty bash`. Check [here](./slurm.md) for detail.
2. create several `tmux` windows. a recap of tmux usage. Check <https://danielmiessler.com/study/tmux/> for more details.
   the purpose of using `tmux` is having multiple shell sessions. If you can achieve it via other ways, it's fine too.
    * Use `tmux` to create a new session
    * Press `Ctrl+b c` to create a new window. 
    * Toggle between the windows by pressing `Ctrl+b <session no>`
    * close a window by pressing `Ctrl+b x`.
3. In one session (such as 0), run `~/DevOps/connection_scripts/slurm_create_one_port_mapping.sh` for SSH mapping from compute node to head node. You will see some port number given to you, such as `8896`. Denote it as `PORT`. **Keep this session open when running Jupyter**. You should see something like this.
   ~~~
   Paste ssh command in a terminal on local host (i.e., laptop)
     ------------------------------------------------------------
     ssh -N -L 8896:localhost:8896 yimengzh@psych-o.hpc1.cs.cmu.edu

     Open this address in a browser on local host; see token below
     ------------------------------------------------------------
     localhost:8896
   In the end, run kill $(lsof -t -i:8896) for potential needed cleanup
   ~~~
   if it also says something like `forward maping to port XXX` fails, that means that port is either already occupied on this node, or some other compute node. Just stop the command and retry until you succeed. Check **CLEANUP** below on how to fix the problem permanently. It's easier to diagnose this problem, if you create these occupied ports yourself on the same compute node. If other people create them, or they are created on other nodes, then it's more difficult to diagnose. It would be nice for SCS to have some mechanism to check all used ports over all nodes at any given time.
4. The output of the above script should ask you to run a command like `ssh -N -L <PORT>:localhost:<PORT> <username>@psych-o.hpc1.cs.cmu.edu`. Go to your local terminal (on your laptop) and run it. **Keep this terminal open when running Jupyter.**
5. Go into another `tmux` session (such as 1), active an appropriate Python environment, (optionally) set up all needed environment variables, and run `jupyter notebook --no-browser --port=<PORT>` to open a jupyter notebook on the server
6. Open `http://localhost:<PORT>` on local browser to use the jupyter notebook on your local computer
7. **CLEANUP** When everything is finished, remember to kill the following things.
    * `ssh` command on your local terminal
    * `ssh` in the first session of the compute node. You **must** also run `kill $(lsof -t -i:<PORT>)` in the same session as an additional safety net. Otherwise, available ports may get fewer and fewer. After running this command, you may or may not get any output. Ignore that. Just remember to always run it after stopping the `ssh` in the compute node.
    * if you forget to do `kill $(lsof -t -i:<PORT>)`, and find ports fewer and fewer, you can also use `ps aux | grep ssh` (on compute nodes) to check whether you have some zombie `ssh` commands left, track their process ids, and use `kill` to kill them. If these occupied ports are due to ssh commands on other nodes, you need to go to other nodes.
    * `jupyter`.
