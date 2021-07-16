# Modify Users

In addition to modifying users in the Azure Portal, we can also modify users through Powershell or the Graph API. I will provide examples here as seen in images I've posted to Twitter.

## Az Powershell Module

Not much useful here. You can change DisplayName, enable/disable the account, and reset the password.

Update-AzADUser Docs:  
<https://docs.microsoft.com/en-us/powershell/module/az.resources/update-azaduser?view=azps-6.2.1>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzAccount

# Shows the syntax along with additional information about Update-AzADUser
Get-Command Update-AzADUser -ShowCommandInfo

# Example changing display name
Update-AzADUser -UserPrincipalName "tuser1@domain.onmicrosoft.com" -DisplayName "Test User One"
````

## Azure AD Module

You'll notice the Azure AD Module has a lot more options when it comes to editing user (and group) attributes.

Set-AzureADUser Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureaduser?view=azureadps-2.0-preview>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about Set-AzureADUser
Get-Command Set-AzureADUser -ShowCommandInfo

# Example of just a few attributes editable by the Azure AD module
Set-AzureADUser -ObjectId "tuser2@domain.onmicrosoft.com" -City "Portland" -CompanyName "Get Securer" -Department "Security" -DisplayName "Test User Two" -GivenName "Test" -Surname "User Two" -JobTitle "Testing"
````

## MSOnline Module

MSOnline handles a lot of the same attributes as the AzureAD modules. I tend to prefer the AzureAD modules as the MSOnline are older and more likely to be deprecated sooner (personal opinion).

Set-MsolUser Docs: <https://docs.microsoft.com/en-us/powershell/module/msonline/set-msoluser?view=azureadps-1.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-MsolService

# Shows the syntax along with additional information about Set-MsolUser
Get-Command Set-MsolUser -ShowCommandInfo

# Example of just a few attributes editable by the MSOnline module
Set-MsolUser -UserPrincipalName "tuser3@domain.com" -City "Portland" -Department "Security" -DisplayName "Test User Three" -FirstName "Test" -LastName "User Three" -UserType "Viral"
````
