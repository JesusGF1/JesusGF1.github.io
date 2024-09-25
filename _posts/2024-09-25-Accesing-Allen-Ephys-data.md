https://allensdk.readthedocs.io/en/latest/install.html

Create a new conda environment and install the AllenSDK using pip

conda create -n allensdk
conda activate allensdk
pip install allensdk
Add conda env to ipykernel so that the notebook can use it

pip install ipykernel
python -m ipykernel install --user --name=allensdk


https://allensdk.readthedocs.io/en/latest/visual_coding_neuropixels.html
