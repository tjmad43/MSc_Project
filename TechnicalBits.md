### installing uproot:
	pip install uproot awkward
-> seems to work ✓


### installing ROOT:
check current version: <br>
  `root —version`
 -> ROOT VERSION: 6.30/02
 
however in Jupyter notebook: <br>
  `import ROOT`
  -> ModuleNotFoundError <br>
because of conda environment? or installed in the wrong place?

tried installing in a different way <br>
  `conda install conda-forge::root`
  -> command taking too long, will probably fail

set up a conda environment and use in target notebook with ipykernel <br>
first attempt, using [this](https://saturncloud.io/blog/how-to-use-conda-environment-in-a-jupyter-notebook/) method, failed: <br>
  `conda create -n myenv python=3.9`<br>
  `conda activate myenv`<br>
  `conda install root`
  -> PackagesNotFoundError

instead using [this](https://iscinumpy.gitlab.io/post/root-conda/) tutorial: <br>
  `conda create -n my_root_env root -c conda-forge`
  -> command successful, new packages installed this time <br>
  `conda activate my_root_env`

now install ipykernel: <br>
  `conda install ipykernel` <br>
  `python -m ipykernel install --user --name=my_root_env` <br>
  in Jupyter notebook select my_root_env as kernel

-> still getting ModuleNotFoundError when importing ROOT in notebook <br>
  missed one command! <br>
  `conda config --env --add channels conda-forge`

now in Jupyter notebook: <br>
  `import ROOT`
  -> Welcome to JupyROOT 6.30/02 <br>
  success!
 
