# kicombo-devops-1
Create a Flask app using Azure App Service on Linux.

This file contains key points from [https://docs.microsoft.com/en-us/azure/app-service/quickstart-python?tabs=bash&pivots=python-framework-flask], a nice tutorial from microsoft's Azure docs.

Azure App Service is an HTTP-based service for hosting web applications, REST APIs, and mobile back ends. Applications run and scale with ease on both Windows and Linux-based environments.

## App Service on Linux
App Service on Linux supports a number of language specific built-in images. Just deploy your code. Supported languages include: Node.js, Java (JRE 8 & JRE 11), PHP, Python, .NET Core and Ruby. Run az webapp list-runtimes --linux to view the latest languages and supported versions. If the runtime your application requires is not supported in the built-in images, you can deploy it with a custom container.

Outdated runtimes are periodically removed from the Web Apps Create and Configuration blades in the Portal. These runtimes are hidden from the Portal when they are deprecated by the maintaining organization or found to have significant vulnerabilities. These options are hidden to guide customers to the latest runtimes where they will be the most successful.

When an outdated runtime is hidden from the Portal, any of your existing sites using that version will continue to run. If a runtime is fully removed from the App Service platform, your Azure subscription owner(s) will receive an email notice before the removal.

If you need to create another web app with an outdated runtime version that is no longer shown on the Portal see the language configuration guides for instructions on how to get the runtime version of your site. You can use the Azure CLI to create another site with the same runtime. Alternatively, you can use the Export Template button on the web app blade in the Portal to export an ARM template of the site. You can re-use this template to deploy a new site with the same runtime and configuration.

## Set up your initial environment
1. Have an Azure account with an active subscription. Create an account for free.
2. Install Python 3.6 or higher.
3. Install the Azure CLI 2.0.80 or higher, with which you run commands in any shell to provision and configure Azure resources.

## Install the Azure CLI on Linux
Run `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash` in terminal. Use `sudo dpkg --configure -a` if necessary.

It takes some time, so please stay patient. After installation, run `az --version` or `az version` to check if everything works fine.

Then sign in to Azure through the CLI:
```bash
az login
```
This command opens a browser to gather your credentials. When the command finishes, it shows JSON output containing information about your subscriptions.

Once signed in, you can run Azure commands with the Azure CLI to work with resources in your subscription.

## Clone and run sample repo into your computer
Clone
```bash
git clone https://github.com/Azure-Samples/python-docs-hello-world
```
Then run
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
flask run
```

## Deploy the sample
Deploy the code in your local folder (python-docs-hello-world) using the `az webapp up` command:
```bash
az webapp up --sku B1 --name <app-name>
```
* If the az command isn't recognized, be sure you have the Azure CLI installed as described in Set up your initial environment.
* If the webapp command isn't recognized, because that your Azure CLI version is 2.0.80 or higher. If not, install the latest version.
* Replace <app_name> with a name that's unique across all of Azure (valid characters are a-z, 0-9, and -). A good pattern is to use a combination of your company name and an app identifier.
* The --sku B1 argument creates the web app on the Basic pricing tier, which incurs a small hourly cost. Omit this argument to use a faster premium tier.
* You can optionally include the argument --location <location-name> where <location_name> is an available Azure region. You can retrieve a list of allowable regions for your Azure account by running the az account list-locations command.

To redeploy, save your changes, then use the `az webapp up` command again:
```bash
az webapp up
```
This command uses values that are cached locally in the .azure/config file, including the app name, resource group, and App Service plan.

## Clean up resources
In the preceding steps, you created Azure resources in a resource group. The resource group has a name like "appsvc_rg_Linux_CentralUS" depending on your location. If you keep the web app running, you will incur some ongoing costs.

If you don't expect to need these resources in the future, delete the resource group by running the following command:
```bash
az group delete --no-wait
```
The command uses the resource group name cached in the .azure/config file.

The --no-wait argument allows the command to return before the operation is complete.
