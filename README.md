# Techbash MLOps Workshop

This repository contains the code and instructions for the Techbash MLOps workshop.

## Setup

### Prerequisites

1. [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
2. [Azure Subscription](https://azure.microsoft.com/en-us/free/) with Owner permissions
3. [Git](https://git-scm.com/download)
4. [GitHub Account](https://github.com)
5. Administrator rights to your computer (the ability to install software)
6. [Python 3.12.0](https://www.python.org/downloads/)
7. [Visual Studio Code](https://code.visualstudio.com/Download):
   1. [Jupyter extension](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
   2. [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

## Preparing for the challenge

Prepare your environment for the challenge by following the instructions in the [Create challenge repository](docs/create_challenge_repository.md) document.

## Helpful learning resources

This learning path goes hand-in-hand with the challenges and provides additional context. A lot of the content mimics what is requested in the challenges. If you are entirely new to Azure Machine Learning, I highly recommend going through this learning path. I will be here to answer any questions along the way if you choose this path.

[End-to-end machine learning operations (MLOps) with Azure Machine Learning](https://learn.microsoft.com/en-us/training/paths/build-first-machine-operations-workflow/)

## Bring on the challenges!

### Challenge 0: Convert a notebook to production code

Scenario Details: [Understand the business problem](https://learn.microsoft.com/en-us/training/modules/use-azure-machine-learn-job-for-automation/2-understand-business-problem)

Challenge Details: [Convert a notebook to production code](https://microsoftlearning.github.io/mslearn-mlops/documentation/00-script.html)

Solution walkthrough: [SPOILERS](docs/challenge_0_solution.md)

### Challenge 1: Create an Azure Machine Learning job

Now we get to delve into the architecture and resources needed to support MLOps.

>**Note**: As part of this challenge,you'll need to setup the infrastructure in Azure. Do this in any way that you are comfortable, using the portal, Azure CLI, PowerShell, Terraform, etc.

Review the solution architecture: [Explore the solution architecture](https://learn.microsoft.com/en-us/training/modules/use-azure-machine-learn-job-for-automation/3-explore-solution-architecture)

Challenge Details: [Create an Azure Machine Learning job](https://microsoftlearning.github.io/mslearn-mlops/documentation/01-aml-job.html).

Solution walkthrough: [SPOILERS](docs/challenge_1_walkthrough.md)

### Challenge 2: Trigger the Azure Machine Learning job with GitHub Actions

Now let's get into the automation. We'll use GitHub actions to setup a workflow that provisions a server and submits a a job using Service Principal credentials.

Scenario Details: [Understand the business problem](https://learn.microsoft.com/en-us/training/modules/trigger-azure-machine-learn-jobs-github-actions/2-understand-business-problem)

Review the solution architecture: [Explore the solution architecture](https://learn.microsoft.com/en-us/training/modules/trigger-azure-machine-learn-jobs-github-actions/3-explore-solution-architecture)

Challenge Details: [Trigger the Azure Machine Learning job with GitHub Actions](https://microsoftlearning.github.io/mslearn-mlops/documentation/02-github-actions.html)

Solution walkthrough: [SPOILERS](docs/challenge_2_walkthrough.md)

### Challenge 3: Trigger GitHub Actions with feature-based development

We want some control over when we trigger the training of our models. To do this, we'll protect our main branch in the repository, so that all work needs to be reviewed and approved before being merged in.

Scenario details: [Understand the business problem](https://learn.microsoft.com/en-us/training/modules/trigger-github-actions-trunk-based-development/2-understand-business-problem)

Review the solution architecture: [Explore the solution architecture](https://learn.microsoft.com/en-us/training/modules/trigger-github-actions-trunk-based-development/3-explore-solution-architecture)

Challenge details: [Trigger GitHub Actions with feature-based development](https://microsoftlearning.github.io/mslearn-mlops/documentation/03-trigger-workflow.html)

Solution walkthrough: [SPOILERS](docs/challenge_3_walkthrough.md)

### Challenge 4: Work with linting and unit testing

We want to ensure that our code is of high quality. To do this, we'll add linting and unit testing to our workflow and ensure these checks are done prior to merging our code.

Scenario details: [Understand the business problem](https://learn.microsoft.com/en-us/training/modules/work-linting-unit-test-github-actions/2-understand-business-problem)

Review the solution architecture: [Explore the solution architecture](https://learn.microsoft.com/en-us/training/modules/work-linting-unit-test-github-actions/3-explore-solution-architecture)

Challenge details: [Work with linting and unit testing](https://microsoftlearning.github.io/mslearn-mlops/documentation/04-unit-test-linting.html)

Solution walkthrough: [SPOILERS](docs/challenge_4_walkthrough.md)

### Challenge 5: Work with environments

In the "real world", we typically have multiple environments, such as dev, test, qa and production. It would be ideal to be able to automate the deployment of our models to the various environments using environment variables that differ for each one.

Gate-checks are also a common practice. We want to ensure that our code is reviewed and approved before it is deployed to various environments. It is highly recommended that any push to a production environment is done with specific approval (rather than automated on push).

Scenario details: [Understand the business problem](https://learn.microsoft.com/en-us/training/modules/work-environments-github-actions/2-understand-business-problem)

Review the solution architecture: [Explore the solution architecture](https://learn.microsoft.com/en-us/training/modules/work-environments-github-actions/3-explore-solution-architecture)

Challenge details: [Work with environments](https://microsoftlearning.github.io/mslearn-mlops/documentation/05-environments.html)

Solution walkthrough: [SPOILERS](docs/challenge_5_walkthrough.md)

### Challenge 6: Deploy and test the model

What good is a model if we can't use it? In this challenge, we'll deploy our model to an Azure Managed Endpoint and test it using a REST API.

Scenario details: [Understand the business problem](https://learn.microsoft.com/en-us/training/modules/deploy-model-github-actions/2-understand-business-problem)

Review the solution architecture: [Explore the solution architecture](https://learn.microsoft.com/en-us/training/modules/deploy-model-github-actions/3-explore-solution-architecture)

Challenge details: [Deploy and test the model](https://microsoftlearning.github.io/mslearn-mlops/documentation/06-deploy-model.html)

Solution walkthrough: [SPOILERS](docs/challenge_6_walkthrough.md)

## Clean up

Delete the resource group that you created in Challenge 1 - this resource group contains all services deployed throughout this workshop.

In the Azure Portal, locate the Microsoft Entra ID service. From the left menu, select **App registrations**, select to view all applications. Locate the **diabetes-dev-svcid** and delete it.

In GitHub, locate your repository, select **Settings**, scroll to the bottom and select **Delete this repository**.

## Conclusion

Congratulations on completing all of the challenges in this MLOps workshop. You now know how to automate a machine learning workflow using GitHub Actions and Azure Machine Learning end-to-end. You can now take this knowledge and apply it to your own projects.
