# Machine learning models for drug discovery
Machine learning models which are trained on PubChem datasets `AID 2100` and `AID 2242` to obtain drug candidates (activators and inhibitors of alpha glucosidase) for Type II diabetes and Pompe's disease.
`AID 2100` and `AID 2242` are PubChem datasets for inhibitors and activators of Human Alpha-glucosidase enzyme respectively. 

Mold2 was used to compute 777 molecular descriptors of the compounds obtained from PubChem. These molecular descriptors were used to train different ML algorithms to predict whether a given compound is an activator/inhibitor of Alpha-glucosidase.

### Steps to run
- Download the PubChem datasets for actives and inactive compounds for `AID 2100` and `AID 2242`
- Compute the molecular descriptors of the compounds with Mold2
- Create virtual environment by running either `python -m venv <name-of-virtual-environment>` or `virtualenv <name-of-virtual-environment>`. Virtualenv can be installed with pip.
- Activate the virtual environment. on Windows, run the following command in Powershell in the root directory. `.\<name-of-virtual-environment>\Scripts\activate`
- After the virtual environment is activated, install all the dependencies for this projects by running `pip install -r requirements.txt` in the root directory
- Run `jupyter notebook` in the root directory. If you don't already have Jupyter notebooks, you can install by running `pip install jupyterlab`

### Understanding the structure of the models
Due to the data imbalance between the `active` and `inactive` compounds, `synthetic minority oversampling technique` (SMOTE) was used. 

Each algorithm is trained with 3 different approaches for the activators and those same 3 approaches for the inhibitors. ie. 6 models for each algorithm
- The first approach uses `ALL` training examples from the `inactive` compounds and performs SMOTE on the `active` compounds. Format for naming: `<activators|inhibitors_over.ipynb>`
- The second approach randomly samples part of the `inactive` compounds and performs SMOTE on the `active` compounds. This approach is similar to the first except it has fewer synthetic training examples for the `active` compounds. Format for naming: `<activators|inhibitors_mid.ipynb>`
- The third approach randomly samples just the exact amount of `inactive` compounds as the `active` compounds to achieve balance. Format for naming: `<activators|inhibitors_under.ipynb>`
