# Modify Groups

In addition to modifying Groups in the Azure Portal, we can also modify Groups through Powershell or the Graph API. I will provide examples here as seen in images I've posted to Twitter.

## Az Powershell Module

This module does not provide the ability to modify group properties (that I'm aware of). There is no Set-AzADGroup or Update-AzADGroup option, but there is an Add-AzADGroupMember if you want to put users in the group

Add-AzADGroupMember Docs:  
<https://docs.microsoft.com/en-us/powershell/module/az.resources/update-azadgroupmember?view=azps-6.2.1>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzAccount

# Shows the syntax along with additional information about Add-AzADGroupMember
Get-Command Add-AzADGroupMember -ShowCommandInfo

# Adding Test User 1 to Test Group 1
Add-AzADGroupMember -MemberUserPrincipalName "tuser1@domain.onmicrosoft.com" -TargetGroupDisplayName "Test Group 1" -Verbose
````

## Azure AD Module

The Azure AD module actually has several cmdlets to deal with group membership, ownership, and attributes for both assigned and dynamic groups! They do require a little extra effort to use some of them as they rely on ObjectId. I've provided examples so you can see how to get those.

Add-AzureADGroupMember Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/add-azureadgroupmember?view=azureadps-2.0-preview>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Add-AzureADGroupMember
Get-Command Add-AzureADGroupMember -ShowCommandInfo

# Adding Test User 2 to Test Group 2
Add-AzureADGroupMember -ObjectId (Get-AzureADGroup -SearchString "Test Group 2").ObjectId -RefObjectId (Get-AzureADUser -SearchString "tuser2@domain.onmicrosoft.com").ObjectId -Verbose
````

Add-AzureADGroupOwner Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/add-azureadgroupowner?view=azureadps-2.0-preview>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Add-AzureADGroupOwner
Get-Command Add-AzureADGroupOwner -ShowCommandInfo

# Making Test User 2 the Owner of Test Group 2
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup -SearchString "Test Group 2").ObjectId -RefObjectId (Get-AzureADUser -SearchString "tuser2@domain.onmicrosoft.com").ObjectId -Verbose
````

Set-AzureADGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup?view=azureadps-2.0-preview>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Set-AzureADGroup
Get-Command Set-AzureADGroup -ShowCommandInfo

# Example of just a few attributes editable by the Azure AD module
Set-AzureADGroup -ObjectId (Get-AzureADGroup -SearchString "Test Group 2").ObjectId -Description "Test Group 2 - Modified" -DisplayName "Test Group 2 - Modified" -MailEnabled $false -Verbose
````

Set-AzureADMSGroup Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadmsgroup?view=azureadps-2.0-preview>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Set-AzureADMSGroup
Get-Command Set-AzureADMSGroup -ShowCommandInfo

# Example of just a few attributes editable by the Azure AD module
Set-AzureADMSGroup -Id (Get-AzureADGroup -SearchString "Security Analysts - UK").ObjectId -Description "All security analysts in the UK" -MembershipRule '(user.country -eq "United Kingdom") and (user.jobTitle -contains "Security Analyst") and (user.accountEnabled -eq True)' -Verbose
````

## MSOnline Module

MSOnline module is pretty useless here. I tend to prefer the AzureAD modules as the MSOnline are older and more likely to be deprecated sooner (personal opinion).

Set-MsolGroup Docs: <https://docs.microsoft.com/en-us/powershell/module/msonline/set-msolgroup?view=azureadps-1.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-MsolService

# Shows the syntax along with additional information about Set-MsolGroup
Get-Command Set-MsolGroup -ShowCommandInfo

# Example of just a few attributes editable by the MSOnline module
Set-MsolGroup -ObjectId (Get-MsolGroup -SearchString "Test Group 3").ObjectId -DisplayName "Test Group 3 - Modified" -Verbose
````
