# Get Groups

In addition to viewing groups in the Azure Portal, we can also get group details through Powershell or the Graph API. I will provide examples here as seen in images I've posted to Twitter.

## Az Powershell Module

This gives you the option to get groups by ObjectId, DisplayNameStartsWith, or DisplayName

Get-AzADGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/az.resources/get-azadgroup?view=azps-6.2.1>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzAccount

# Shows the syntax along with additional information about Get-AzADGroup
Get-Command Get-AzADGroup -ShowCommandInfo

# Excact match on DisplayName, could use DisplayNameStartsWith for parial matches or ObjectId if known
Get-AzADGroup -DisplayName "Test Group 1" | fl *
````

## Azure AD Module

With this module, you will use the SearchString parameter, but if you need all groups, you'll have to specify -All $true. Get-AzureADMSGroup is newer and supports dynamic group membership information.

Get-AzureADGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/get-azureadgroup?view=azureadps-2.0-preview>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Get-AzureADGroup
Get-Command Get-AzureADGroup -ShowCommandInfo

# Example using SearchString for "Test Group 2"
Get-AzureADGroup -SearchString "Test Group 2" | fl *
````

Get-AzureADMSGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/get-azureadgroup?view=azureadps-2.0-preview>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Get-AzureADGroup
Get-Command Get-AzureADMSGroup -ShowCommandInfo

# Example using SearchString for "Security Analysts - UK"
Get-AzureADMSGroup -SearchString "Security Analysts - UK" | fl *
````

## MSOnline Module

Get-MsolGroup Docs: <https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup?view=azureadps-1.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-MsolService

# Shows the syntax along with additional information about Get-MsolGroup
Get-Command Get-MsolGroup -ShowCommandInfo

# Example using SearchString for "Test Group 3", could also use 
Get-MsolGroup -SearchString "Test Group 3" | fl *
````
