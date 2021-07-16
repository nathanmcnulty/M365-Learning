# Create Users

In addition to creating users in the Azure Portal, we can also create users through Powershell or the Graph API. I will provide examples here as seen in images I've posted to Twitter.

## Az Powershell Module

New-AzADUser Docs:  
<https://docs.microsoft.com/en-us/powershell/module/az.resources/new-azaduser?view=azps-6.2.1>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzAccount

# Shows the syntax along with additional information about New-AzADUser
Get-Command New-AzADUser -ShowCommandInfo

# Creates a new user and accepts input from the console for the password
New-AzADUser -DisplayName "Test User 1" -UserPrincipalName "tuser1@domain.onmicrosoft.com" -Password (Read-Host -AsSecureString) -MailNickname "tuser1"
````

## Azure AD Module

New-AzureADUser Docs:  
<https://docs.microsoft.com/en-us/powershell/module/azuread/new-azureaduser?view=azureadps-2.0-preview>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-AzureAD

# Shows the syntax along with additional information about New-AzureADUser
Get-Command New-AzureADUser -ShowCommandInfo

# New-AzureADUser does not support entering a password directly, so we have to use a PasswordProfile object
$PasswordProfile = New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password = "Haha, nice try!"

# Creates a new user and uses the password from above
New-AzureADUser -AccountEnabled $true -DisplayName "Test User 2" -PasswordProfile $PasswordProfile -GivenName "Test" -MailNickName "tuser2" -Surname "User 2" -UsageLocation "US" -UserPrincipalName "tuser2@domain.onmicrosoft.com"
````

## MSOnline Module

New-MsolUser Docs:  
<https://docs.microsoft.com/en-us/powershell/module/msonline/new-msoluser?view=azureadps-1.0>

````Powershell
# Need to authenticate to our tenant with the correct account
Connect-MsolService

# Shows the syntax along with additional information about New-MsolUser
Get-Command New-MsolUser -ShowCommandInfo

# Creates a new user and accepts input from the console for the password
New-MsolUser -UserPrincipalName "tuser3@domain.onmicrosoft.com" -DisplayName "Test User 3" -FirstName "Test" -LastName "User 3" -UsageLocation "US" -Password (Read-Host -AsSecureString)
````
