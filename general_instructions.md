# Usage Example
To list, import, and download the datasets registered here, please see a usage example [here](https://github.com/nd-crane/raite-data-registry-usage-example). 

# Data Registry Maintenance

Add, pull, and update data in that RAITE dataset registry. For more information about data registry, go to [https://dvc.org/doc/use-cases/data-registry](https://dvc.org/doc/use-cases/data-registry).

**Note**: To access this dataset registry, you must have SSH access to *CRC machines*.
We will add another remote location with an access type other than an SSH-dependent one so that users outside of Notre Dame have access.

### **Setup**

The requirement is to clone this repo and have DVC installed.

**1. Cloning this repo**
```bash
git clone https://github.com/nd-crane/raite-data-registry.git
cd raite-data-registry
```

**2. Installing DVC**

You can find instructions [here](https://dvc.org/doc/install) on how to install DVC.

If installing with conda it is recommeneded to set your default solver as libmamba. You can find instructions [here](https://www.anaconda.com/blog/conda-is-fast-now) on installing and setting your default solver as libmamba. Alternatively, you can also follow the DVC installation instructions and install mamba within your DVC envirnoment.

#### Installing with conda (libmamba default solver):

###### Local storage
```bash
conda install -c conda-forge dvc
```

###### Remote storage
```bash
conda install -c conda-forge dvc-ssh
```

###### Google Drive
```bash
conda install -c conda-forge dvc-gdrive
```

#### Installing with conda (libmamba not default solver):

Start by installing mamba as the default solver in your DVC envirnoment.

###### Mamba solver

```bash
conda install -c conda-forge mamba
```
Use the `mamba` command to install DVC.

###### Local storage
```bash
mamba install -c conda-forge dvc
```

###### Remote storage
```bash
mamba install -c conda-forge dvc-ssh
```

###### Google Drive
```bash
mamba install -c conda-forge dvc-gdrive
```

#### Installing with Pip:

###### Local storage
```bash
pip install dvc
```
###### Remote storage
```bash
pip install dvc[ssh]
```
###### Google Drive
```bash
pip install dvc[gdrive] 
```
#### PDM:

Or, if you use PDM to manage Python packages, after cloning this repo, you can have DVC by running the following command.

```bash 
pdm update
```

*Note*: Remember to add `pdm run` at the beginning of the DVC commands. 


### **Adding datasets to this registry**

You can add your dataset to this [data registry](https://dvc.org/doc/use-cases/data-registry) by running the following steps:

**1. Copy your dataset**
Copy your dataset to `./data/ folder, for example:

```bash
cp ~/Downloads/<your-dataset-name> ./data/
```

**1. Add your dataset to DVC:**

```bash
dvc add data/<your-dataset-name>
dvc push
```
**2. Add your dataset metadata to Git:**
```bash
git add data/<your-dataset-name>.dvc
git add data/.gitignore
git commit -m "Add <your-dataset-name>"
git push
```


### **Pulling data**

To pull all the registered data, run the following commands:

```bash
dvc pull 
```

To pull a specific dataset, for example, the initial crane dataset, you can run the following command:

```bash
dvc pull data/raite_2023
```

