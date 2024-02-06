
# RAITE Dataset Registry

This repository contains the RAITE [data registry](https://dvc.org/doc/use-cases/data-registry). It is a [DVC](https://dvc.org/) repository that contains the metadata of the datasets used in the RAITE project.


## How to use 
You can use this repository to list, import, and download the datasets used in the RAITE. You don't need to clone this repository for that.
You only need to have DVC installed.

Please follow the instructions [here](https://dvc.org/doc/install) to install DVC.

**Note**: For now, to access this dataset registry, you need to have ssh access to *CRC machines*.

We will add another remote location with an access type other than SSH dependent one so that users outside of Notre Dame have access.

### **Listing data**

To explore the currently available datasets of this DVC repository, you can run the `dvc list` command over the folder `data` as follows:

```bash
dvc list https://github.com/nd-crane/raite-data-registry data/
```

To view the content of a particular dataset in the registry, you can run the `dvc list` with `-R` and specify the dataset name in the data folder. 
For example, to list the content of the initial crane dataset, you can run the following command:

```bash
dvc list -R https://github.com/nd-crane/raite-data-registry data/raite_2023
```

### **Data import workflow**
You can import a specific dataset from the registry by running the `dvc import` command. It is analogous to using direct download tools like wget (HTTP).
For example, to import the initial crane dataset, you can run the following:

```bash
# Only in the first time
dvc init
```

```bash
dvc import  https://github.com/nd-crane/raite-data-registry data/raite_2023
```

Besides downloading the data, `dvc import` saves information about the dependency that the local project has on the data source (the raite-data-registry repo).
In that case, DVC generates a special import `.dvc` file containing such dependency information. In the previous example, the generated file is `raite_2023.dvc`.

Whenever the dataset changes in the registry, you can bring data up to date with the `dvc update` command followed by the name of the generated `.dvc` file. For example, to update the initial crane dataset, you can run the following:
```bash
dvc update raite_2023.dvc
```

### **Data downloads**
You can download a specific dataset from the registry by running the `dvc get` command. It uses the same syntax as the `dvc import` command but doesn't save the dependency information.

To obtain the initial crane dataset, execute the following command for downloading:

```bash
dvc get  https://github.com/nd-crane/raite-data-registry data/raite_2023
```

## Dataset Registry Maintenance

You can add, pull, and update data in that [data registry](https://dvc.org/doc/use-cases/data-registry) for the RAITE exercise.

**Note**: To access this dataset registry, you need access permission to the *CRC machine*.
We will change the remote location and update the access policy on that page.

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
