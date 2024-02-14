# Mastering Linux

## Deploy vm to use on labs

### Files

- Templates
  - azure-pipelines.yml
  - Templates
    - vmCentOsFresh
      - parameters.json
      - template.json

### Image

CentOS 8 from OpenLogic by Perforce (from Marketplace)

### Steps

- Create GitHub repository that will be the repo for the IAC files (and the application files).
- Create Azure Devops project in the organization.
- Create a Service connection.
- Add the service connection. (set contributor role in the subscription).
- Create a GitHub connection. (for access the GitHub repo).
- Clone the repo to local machine.
- Create IAC code files. (Deploy selected image using portal and download the template files)
- Create YML pipeline file. https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/?view=azure-pipelines
- Validate files using vscode.
- Check the templates using PowerShell What-if command.
- New-AzResourceGroupDeployment -Whatif -ResourceGroupName rgMasteringLinux -TemplateUri "C:\...\template.json" -TemplateParameterFile "C:\...\parameters.json"
- Create a variable group in the devops library to hold deploy sensitive data. (adminPassword) https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/variables
