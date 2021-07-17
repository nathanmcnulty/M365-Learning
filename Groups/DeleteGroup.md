# Delete Groups

In addition to deleting groups in the Azure Portal, we can also delete groups through Powershell or the Graph API. I will provide examples here as seen in images I've posted to Twitter.

## Az Powershell Module

Remove-AzADGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/az.resources/remove-azadgroup?view=azps-6.2.1>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzAccount

# Shows the syntax along with additional information about Remove-AzADGroup
Get-Command Remove-AzADGroup -ShowCommandInfo

# Remove group, add -Force to skip prompt
Remove-AzADGroup -DisplayName "Test Group 1" -Verbose
````

## Azure AD Module

Remove-AzureADGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/remove-azureadgroup?view=azureadps-2.0-preview>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Remove-AzureADGroup
Get-Command Remove-AzureADGroup -ShowCommandInfo

# Remove group, no force needed
Remove-AzureADGroup -ObjectId "tgroup2@domain.onmicrosoft.com"
````

## MSOnline Module

Remove-MsolGroup Docs: <https://docs.microsoft.com/en-us/powershell/module/msonline/remove-msolgroup?view=azureadps-1.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-MsolService

# Shows the syntax along with additional information about Remove-MsolGroup
Get-Command Remove-MsolGroup -ShowCommandInfo

# Remove group, add -Force to skip prompt
Remove-MsolGroup -ObjectId (Get-MsolGroup -SearchString "Test Group 3").ObjectId -Verbose
````
