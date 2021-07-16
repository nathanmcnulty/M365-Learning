# Creating Groups

In addition to creating groups in the Azure Portal, we can also create groups through Powershell or the Graph API. I will provide examples here as seen in images I've posted to Twitter.

## Az Powershell Module

New-AzADGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/az.resources/new-azadgroup?view=azps-6.2.1>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzAccount

# Shows the syntax along with additional information about New-AzADGroup
Get-Command New-AzADGroup -ShowCommandInfo

# Creates a new group
New-AzADGroup -DisplayName "Test Group 1" -MailNickname "TestGroup1"
````

## Azure AD Module

New-AzureADGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/new-azureadgroup?view=azureadps-2.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about New-AzureADGroup
Get-Command New-AzureADGroup -ShowCommandInfo

# Creates a new group that can be used for permissions, -MailEnabled $true not available yet
New-AzureADGroup -DisplayName "Test Group 2" -MailEnabled $false -MailNickname "TestGroup2" -SecurityEnabled $true
````

## MSOnline Module

New-MsolGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/msonline/new-msolgroup?view=azureadps-1.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-MsolService

# Shows the syntax along with additional information about New-MsolGroup
Get-Command New-MsolGroup -ShowCommandInfo

# Creates a new group with a description
New-MsolGroup -DisplayName "Test Group 3" -Description "Test group created with the MSOnline module"
````
