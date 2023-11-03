# Challenge 1: Create an Azure Machine Learning job

This approach will use the CLIv2 to create workspace assets. Ensure you've logged in using `az login` and set the default subscription `az account set -s {SUBSCRIPTION_ID}`. You can continue to use the Visual Studio terminal to run the commands.

## Setup CLI

1. Ensure the Azure CLI is installed, then install the extension, note to remove the azure-cli-ml extension as it conflicts with the new ml extension:

   ```bash
   az extension remove -n azure-cli-ml
   az extension remove -n ml
   az extension add -n ml -y
   ```

## Setup base resources

1. Create a resource group and make it the default:

   ```bash
    az group create --name "diabetes-dev-rg" --location "eastus"
    az configure --defaults group="diabetes-dev-rg"
    ```

2. Create the AML workspace default (so you don't have to specify it on each command):

    ```bash
    az ml workspace create --name "aml-diabetes-dev"
    az configure --defaults workspace="aml-diabetes-dev"
    ```

3. Create a compute instance for running code (--name must be unique in the region):

    ```bash
     az ml compute create --name "testdev-vm-cep" --size STANDARD_DS11_V2 --type ComputeInstance
    ```

4. Open the Machine Learning Studio for the workspace, and note the compute instance that is created in the **Manage/Compute** section.

## Register the dataset using CLI

Registering the dataset using the CLI pointing to a local file will automatically upload it to Azure Machine Learning storage.

1. In the root of the project, create the [challenge1_dataset.yml](../yml/challenge1_dataset.yml) file. Note the name and the location points to the folder.

2. In the terminal, navigate to the root of the project (at the same level as the yml file you just created).

3. Register the dataset using the CLI:

   ```bash
   az ml data create --file challenge1_dataset.yml
   ```

4. In the Azure portal, open the AML workspace you've created and locate the dataset in the **Assets/Data** section.

## Complete the src/job.yml file

Change out to the registered dataset name and version (vs folder URI). Set compute name as the one you created for this lab.

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/commandJob.schema.json
code: model
command: >-
  python train.py
  --training_data ${{inputs.training_data}}
inputs:
  training_data: 
    path: azureml:diabetes-dev-folder:1
    mode: ro_mount 
  reg_rate: 0.01
environment: azureml:AzureML-sklearn-1.0-ubuntu20.04-py38-cpu@latest
compute: azureml:testdev-vm-cep
experiment_name: challenge-1-experiment
description: challenge 1 experiment
```

## Submit job through the CLI

```bash
az ml job create --file src/job.yml
```

Congratulations!! You've submitted the machine learning experiment using the train.py script you created and sent it along to Azure Machine Learning. You can monitor the job in the Machine Learning Studio under the **Assets/Jobs** section.
