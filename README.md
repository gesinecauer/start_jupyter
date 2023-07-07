# start_jupyter

Intended for folks in genome sciences at UW.

## Description

### run_jupyter
This script should only be run on the remote host.
It can be used to submit a JupyterLab job to the grid engine using the specified
parameters.
The name of this job is determined from '-N', -l', '-pe', and '-P' options
(see `run_jupyter -help` for details).
If a job with this same name already exists, the script merely prints
information for the preexisting job - no new job will be submitted.

If you typically use the same options for your jobs and don't want to have to
type them out each time you use this script, modify
`~/.run_jupyter.qsub_option_defaults` on the remote host.

### ssh_jupyter
This script should only be run on your local machine.
It submits a JupyterLab job to the grid engine on the remote host, then
activates JupyterLab by sshing to the remote host at the JupyterLab port and
grid engine node.
This script calls `run_jupyter` on the remote host - most command line options
for `ssh_jupyter` are forwarded to `run_jupyter`.

## Installation

Put `run_jupyter` on your remote host and `ssh_jupyter` on your local machine.
Add both to the `PATH` environment variable in your shell configuration files.

For `ssh_jupyter`, I recommend setting `~/.ssh/config` on your local machine
such that you don't need to type your password every time you ssh to the remote
host.
If you have to connect to a gateway (ie nexus) to reach the head node (ie
grid), you'll probably want to set up local port forwarding as well.

## Usage

Most `qsub` options are supported.
See `run_jupyter -help` and `ssh_jupyter -help` for full usage information.

## Bugs

Feel free to reach out if you run into any problems!
Use at your own risk, ect ect.
