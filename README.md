## Linux VM (to be used in labs)

- azure-pipelines.yml
- Templates
  - vmCentOsFresh
    - parameters.json
    - template.json

[Plan your Linux environment in Azure](https://learn.microsoft.com/en-us/training/modules/plan-your-linux-environment-in-azure/)

### Image

- CentOS 8
  - [image](https://azuremarketplace.microsoft.com/en-us/marketplace/apps?search=CentOS%208%20from%20OpenLogic%20by%20Perforce&page=1)

### References

- Create GitHub project repository that will be the repo for the IAC files used by the pipeline.
- Create Azure Devops project.
- Create a Service connection.
- Add the service connection and set contributor role for into the subscription.
- Create a GitHub connection to the project where the files are stored.
- Clone the repo to local machine.
- VSCode Extensions
  - [Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-azure-devops.azure-pipelines)
  - [Azure PowerShell Tools](https://marketplace.visualstudio.com/items?itemName=azps-tools.azps-tools)
  - [Azure Resource Manager (ARM) Tools](https://marketplace.visualstudio.com/items?itemName=msazurermtools.azurerm-vscode-tools)
  - [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- Create IAC code files. (Deploy selected image using portal and download the template files)
- Create a variable group in the devops library to hold deploy sensitive data.
- Create YML pipeline file.
  - [YAML schema reference for Azure Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/?view=azure-pipelines)
  - [Variables in ARM templates](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/variables)
  - [Parameters in ARM templates](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/parameters)
  - [Add & use variable groups](https://learn.microsoft.com/en-us/azure/devops/pipelines/library/variable-groups?view=azure-devops&tabs=yaml)
  - [AzureResourceGroupDeployment@2 - Azure resource group deployment v2 task](https://learn.microsoft.com/en-us/azure/devops/pipelines/tasks/reference/azure-resource-group-deployment-v2?view=azure-pipelines&viewFallbackFrom=azure-devops)
- Check the templates using PowerShell What-if command.
  - [ARM template deployment what-if operation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/deploy-what-if?tabs=azure-powershell)
- Create and run Pipeline in Azure Devops project.
  - [Review logs to diagnose pipeline issues](https://learn.microsoft.com/en-us/azure/devops/pipelines/troubleshooting/review-logs?view=azure-devops)
