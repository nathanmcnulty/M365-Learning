# Microsoft 365 Powershell Modules

This is where I will put the information for varoius Powershell modules I cover along with some details of where you might want to use them, installation, and always a link to the documenation.
<p>&nbsp;</p>

## Azure Az Powershell Module

I find these modules a little more difficult to work with in relation to Azure AD, but if you use a lot of other Azure resources, such as IaaS/PaaS offerings, this might be the best choice for you. It can be particularly helpful when dealing with subscriptions, IAM, etc.
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

I find these to be the easiest to work with, and I tend to prefer the Preview module which  has support for newer features sooner. If you will be working primarily in Azure AD and not in other Azure components, this might be the best choice for you.
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

