
# RAITE Dataset Registry

This repository contains the RAITE [data registry](https://dvc.org/doc/use-cases/data-registry). It is a [DVC](https://dvc.org/) repository that contains the metadata of the datasets used in the RAITE project.


## Usage Example
To list, import, and download the datasets registered here, please see [a usage example here](https://github.com/nd-crane/raite-data-registry-usage-example) 

## Dataset Registry Maintenance

You can add, pull, and update data in that RAITE dataset registry. For more information about data registry go to [https://dvc.org/doc/use-cases/data-registry](https://dvc.org/doc/use-cases/data-registry)

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

You can find instructions [here](https://dvc.org/doc/install) to install DVC.

If you decide to use PDM to manage Python packages, after cloning this repo, you can have DVC by running this command:

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
