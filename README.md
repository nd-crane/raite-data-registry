
# RAITE Dataset Registry

This repository contains the RAITE dataset registry. It is a [DVC](https://dvc.org/) repository that contains the metadata of the datasets used in the RAITE project.


## How to use 
You can use this repository to list, import, and download the datasets used in the RAITE project. You don't need to clone this repository for that.
You only need to have DVC installed.

Please follow the instructions [here](https://dvc.org/doc/install) to install DVC.

### **Listing data**

To explore the currently available datasets of this DVC repository, you can run the `dvc list` command over the folder `data` as follows:

```bash
dvc list https://github.com/nd-crane/raite-data-registry data/
```

To view the content of a particular dataset in the registry, you can run the `dvc list` with `-R` and specify the dataset name in the data folder. 
For example, to list the content of the initial crane dataset, you can run the following command:

```bash
dvc list -R https://github.com/nd-crane/raite-data-registry data/crane-dataset
```

### **Data import workflow**
You can import a specific dataset from the registry by running the `dvc import` command. It is analogous to using direct download tools like wget (HTTP).
For example, to import the initial crane dataset, you can run the following:

```bash
dvc import  https://github.com/nd-crane/raite-data-registry data/crane-dataset
```

Besides downloading the data, `dvc import` saves the information about the dependency that the local project has on the data source (the raite-data-registry repo).
In that case, DVC generates a special import `.dvc` file, which contains such dependency information. In the previous example, the generated file is `crane-dataset.dvc`.

Whenever the dataset changes in the registry, you can bring data up to date in with `dvc update` command followed by the name of the generated `.dvc` file. For example, to update the initial crane dataset, you can run the following:
```bash
dvc update crane-dataset.dvc
```

### **Data downloads**
You can download a specific dataset from the registry by running the `dvc get` command. It uses the same syntax as `dvc import` command, but it doesn't save the dependency information.

To obtain the initial crane dataset, execute the following command for downloading:

```bash
dvc get  https://github.com/nd-crane/raite-data-registry data/crane-dataset
```




