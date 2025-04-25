# Installation instructions for devbio-napari on clara

These instructions are derived/modified from [this page](https://www.sc.uni-leipzig.de/05_Instructions/Jupyter/#how-to-use-your-own-environments-and-kernels).

Request a [Scientific Computing Account at ULei](https://www.urz.uni-leipzig.de/servicedesk-und-hilfe/hilfe-zu-unseren-services/forschung/hilfe-webbasiertes-data-science-und-machine-learning-mit-jupyter). Use this information when applying:
* Zugang zu den System(en): paula, clara, jupyter
* Projektname: Lecture Bio Image Data Science
* Projektverantwortliche: Robert Haase
* Fakultät: Math/Inf
* Abteilung: ScaDS.AI

Login to VPN and [Jupyter Hub](https://lab.sc.uni-leipzig.de/) and open a terminal.

Install [ana]conda
```
module load Anaconda3
conda init bash
```

At this point, we need to reopen the terminal. Afterwards, create a conda environment with one specific python version only.

```
conda create --name my_first_env python=3.9
```

You can then activate the environment:
```
conda activate my_first_env
```

If an error occors here (`CondaError: Run 'conda init' before 'conda activate'`), you need to call this:
```
eval "$(conda shell.bash hook)"
conda activate my_first_env
```

Install the needed libraries using `pip`:
```
pip install devbio-napari
pip install scikit-image==0.19.3
pip install ipykernel
```

Make this conda environment available to Jupyter hub like this:
```
python -m ipykernel install --user --name 'my_first_env' --display-name "my_first_env"
```

_Sometimes_ this is necessary too:
```
# Reload page (Jupyter hub in browser)
# jupyter labextension install @jupyter-widgets/jupyterlab-manager ipycanvas
```

To make stackview work interactively, install it outside the conda environment:
```
conda deactivate
pip install stackview --user
```
... and reload the page (in browser)


Just in case you want to install more packages later, reopen the terminal, activate the environment and install them:
```
conda activate my_first_env 
pip install other-package
```
