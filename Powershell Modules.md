# Microsoft 365 Powershell Modules

This is where I will put the information for varoius Powershell modules I cover along with some details of where you might want to use them, installation, and always a link to the documenation.
<p>&nbsp;</p>

## Azure Az Powershell Module

These have improved since AzureRM when it comes to Azure AD, and if I had to choose a module to invest time in, I think this would be the best one to choose. You get cross playform support with Powershell 7, and it is able to do both Azure AD as well as other Azure resources, such as IaaS/PaaS offerings - something the other modules cannot do. This is also included in Azure Cloud Shell and has less dependencies when using Azure Automation or Azure Functions.
<p>&nbsp;</p>

## Az Installation

The installation instructions along with the rest of the documentation can be found here: <https://docs.microsoft.com/en-us/powershell/azure/install-az-ps?view=azps-5.9.0#installation>

If you trust a random person on the Internet, here's the install command :)

```Powershell
Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force
```

> Note: You may have to run "Set-ExecutionPolicy Unrestricted" from an elevated Powershell prompt for these to work
<p>&nbsp;</p>

## AzureAD Preview Powershell Module

I tend to prefer the Preview module which has support for newer features sooner. These are a little less flexible than the Az modules and often requires the use of the -All switch. You may find yourself having to query far more than you want and filtering with a " | Where-Object " more often than you'd like. I'd play with both Az and AzurAD modules and see which fits your scenario best.
<p>&nbsp;</p>

## AzureAD Preview Installation

The installation instructions along with the rest of the documentation can be found here: <https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module>

If you trust a random person on the Internet, here's the install command :)

```Powershell
Install-Module AzureADPreview
```

> Note: Requires running Powershell as Admin
<p>&nbsp;</p>

## MSOnline Powershell Module

These modules came before the Az and AzureAD modules and have been largely replaced. There may still some things like licensing that are a little easier to accomplish with these modules, but I wouldn't recommend investing time in them at this point. Just be aware that they exist and might fit a need you have.
<p>&nbsp;</p>

## MSOnline Installation

The installation instructions along with the rest of the documentation can be found here: <https://docs.microsoft.com/en-us/microsoft-365/enterprise/connect-to-microsoft-365-powershell?view=o365-worldwide#step-1-install-the-required-software-1>

If you trust a random person on the Internet, here's the install command :)

```Powershell
Install-Module MSOnline
```

> Note: Requires running Powershell as Admin
<p>&nbsp;</p>

