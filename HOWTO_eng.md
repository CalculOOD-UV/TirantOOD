# Open On Demand Càlcul UV

Open On Demand is an open-source project that allows easy access to supercomputing resources.

## Using the platform

Go to [Tirant OOD](tirantood.uv.es) or [Vives OOD](localhost/#NYI) and log into using the user/password provided by the administrators.

Once logged into the platform the MoD (Message of the Day) will appear as well as the different tabs in the upper-left corner:

<<<<<<< HEAD
_Files, Jobs, Clusters, Interactive Apps, My Interactive Sessions_
=======
_Files, Jobs, Clusters, Interactive Apps, My Interactive Sessions_ 
>>>>>>> 6636e6c (Change in doc)

and in the upper-right corner:

_Help, Your User_ and _Log Out_

Once in the platform we can start a shell to do the necessary steps to be able to use Python.


## Initial Steps

_This is a version of the HOWTO.txt file at storage/apps/MINICONDA/ folder_

To be able to use Python in our user environment we have to load __MINICONDA__:

```bash
module load miniconda/3
```

Once it __conda__ is loaded we have to initialize our shell by executing the following command:

```bash
conda init bash
```

This will write code into __~/.bashrc__ . To make the changes take effect we must log out and log again or ```source ~/.bashrc``` directly without logging out.

Now we can config __conda__:

```bash
conda config
conda config --add envs_dirs /storage/projects/USER_GROUP/VENVS
```

where **USER_GROUP** is our project group name (_usually the first numbers that follow our user LV..._) and **VENVS** the name we want to store the Python environments.

We can also disable the auto-activation of the __conda base environment__ by:

```bash
conda config --set auto_activatde_base false
```

## Creating a Conda Environment

Once configured we can start creating our Conda Environments.

 + To create an environment from scratch:

```bash
conda create -n venv_name python==3.11
```

change **venv_name** and the python version to your needs.

 + To use the environment:

```bash
conda activate venv_name
```

<<<<<<< HEAD
=======
__NOTICE__:  User MUST create a jupyter Env called **Jupyter_ood** to be able to run the Jupyter Notebooks.

>>>>>>> 6636e6c (Change in doc)
 + To save the python module requirements of our environment (reproducible results):

```bash
conda env export > env_file.yml
```

 + To create a conda environment from that file:

```bash
conda env create -n env_name -f env_file.yml
```

## Installing packages

Once we have activated the newly created environment we can install the packages needed to run our python scripts/notebooks.

Specifically, to run Jupyter Notebooks we have to:

```bash
conda install jupyter
```

Other useful packages are:

 + Pandas: for data wrangling
 + Matplotlib/Seaborn: for data visualization
 + Numpy, Numba, Jax: for mathematical operations
 + AI-related: 
    - scikit-learn, pytorch
 + Quantum-related:
    - qiskit, qutip, qibo, pennylane

## Jupyter Notebook

To run a ___Jupyter Notebook___ go to _Interactive Apps_ $\rightarrow$ _Jupyter Notebook_ and select the _Number of cores_ and any _Extra Jupyter Args_ (see [Jupyter Docs](https://docs.jupyter.org/en/latest/use/config.html)).

This will start a Jupyter Notebook server from where we will be able to run our code.

__REMINDER__:  User MUST create a jupyter Env called **Jupyter_ood** to be able to run the Jupyter Notebooks.


## Initializing a Git Repo

A good practice is to have version control of your code, that way you or your team will know what changes have been introduced. Detailed documentation on this is available at [GitHub Docs](https://docs.github.com/en)