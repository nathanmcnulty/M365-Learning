# Delete Users

In addition to deleting users in the Azure Portal, we can also delete users through Powershell or the Graph API. I will provide examples here as seen in images I've posted to Twitter.

## Az Powershell Module

Remove-AzADUser Docs:  
<https://docs.microsoft.com/en-us/powershell/module/az.resources/remove-azaduser?view=azps-5.9.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzAccount

# Shows the syntax along with additional information about Remove-AzADUser
Get-Command Remove-AzADUser -ShowCommandInfo

# Remove user with -Force to skip prompt
Remove-AzADUser Remove-AzADUser -UserPrincipalName "tuser1@domain.onmicrosoft.com" -Force
````

## Azure AD Module

Remove-AzureADUser Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/remove-azureaduser?view=azureadps-2.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Remove-AzureADUser
Get-Command Remove-AzureADUser -ShowCommandInfo

# Remove user, no force needed
Remove-AzureADUser -ObjectId tuser2@domain.onmicrosoft.com
````

## MSOnline Module

Remove-MsolUser Docs: <https://docs.microsoft.com/en-us/powershell/module/msonline/remove-msoluser?view=azureadps-1.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-MsolService

# Shows the syntax along with additional information about Remove-MsolUser
Get-Command Remove-MsolUser -ShowCommandInfo

# Remove user with -Force to skip prompt
Remove-MsolUser -UserPrincipalName tuser3@domain.onmicrosoft.com -Force
````
