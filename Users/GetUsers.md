# Get Users

In addition to viewing users in the Azure Portal, we can also get user details through Powershell or the Graph API. I will provide examples here as seen in images I've posted to Twitter.

## Az Powershell Module

This gives you the option to get users by UserPrincipalName, DisplayName, Mail, and a quasi-filter of StartsWith

Get-AzADUser Docs:  
<https://docs.microsoft.com/en-us/powershell/module/az.resources/get-azaduser?view=azps-5.9.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzAccount

# Shows the syntax along with additional information about Get-AzADUser
Get-Command Get-AzADUser -ShowCommandInfo

# UPN for looking up users, -StartsWith for searches
Get-AzADUser -UserPrincipalName tuser1@domain.onmicrosoft.com
````

## Azure AD Module

With this module, you will mostly use filters with the SearchString parameter.  

Get-AzureADUser Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/get-azureaduser?view=azureadps-2.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Get-AzureADUser
Get-Command Get-AzureADUser -ShowCommandInfo

# Example using SearchString for "tuser2"
Get-AzureADUser -SearchString "tuser2" 
````

## MSOnline Module

Get-MsolUser Docs: <https://docs.microsoft.com/en-us/powershell/module/msonline/get-msoluser?view=azureadps-1.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-MsolService

# Shows the syntax along with additional information about Get-MsolUser
Get-Command Get-MsolUser -ShowCommandInfo

# Example using SearchString for "tuser3"
Get-MsolUser -SearchString "tuser3"
````
