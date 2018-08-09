# Deploy Azure Webapp with an Nginx Reverse Proxy

Scripts and Docker Compose definition for deploying a Java web application container image, or any web
application listening on port 8080 in a container image, with an Nginx Proxy as an Azure Web App.

## Setup

Before deploying, modify the docker-compose.yml file to change the "${IMAGE}" environment variable to
the name of the container image for your web application.

## Usage

### Bash Shell

Execute the "deploy-webapp.sh" script at a command line. The available parameters are:

* -r or --resourcegroup (Default 'myresourcegroup'): Name of the Resource Group to be created.
* -l or --location (Default 'westus'): Location for all resources to be created.
* -s or --appserviceplan (Default 'myappserviceplan'): Name of the App Service Plan to be created.
* -c or --cazurecontainerregistry (Default 'myazurecontainerregistry'): Name of the Azure Container Registry
  to be created. This must be a globally unique name.
* -w or --webapp (Default 'mywebapp'): Name of the Web App Service to be created. This must be a globally
  unique name.

```
.\deploy-webapp.sh --azurecontainerregistry myacr0192837465 --webapp mywebapp-0192837465
```

### Windows PowerShell

Execute the "deploy-webapp.ps1" script in Powershell. The available parameters are:

* resourcegroup (Default 'myresourcegroup'): Name of the Resource Group to be created.
* location (Default 'westus'): Location for all resources to be created.
* appserviceplan (Default 'myappserviceplan'): Name of the App Service Plan to be created.
* azurecontainerregistry (Default 'myazurecontainerregistry'): Name of the Azure Container Registry
  to be created. This must be a globally unique name.
* webapp (Default 'mywebapp'): Name of the Web App Service to be created. This must be a globally
  unique name.

```
.\deploy-webapp.ps1 -azurecontainerregistry myacr0192837465 -webapp mywebapp-0192837465
```

## Accessing Logs

You can view your application's log files by entering this command (Bash or PowerShell), substituting
your resource group name and web app service name instead of "myresourcegroup" and "mywebapp":

```
az webapp log download --resource-group myresourcegroup --name mywebapp
```
