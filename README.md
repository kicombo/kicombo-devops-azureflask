# kicombo-devops-1
Create a Flask app using Azure App Service on Linux.

I followed [https://docs.microsoft.com/en-us/azure/app-service/quickstart-python?tabs=bash&pivots=python-framework-flask], a nice tutorial from microsoft's Azure docs.

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

It takes some time, so please stay patient. After installation, run `az version` to check if everything works fine.
