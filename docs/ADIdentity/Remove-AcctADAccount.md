
# Remove-Acctadaccount
Removes AD computer accounts from an identity pool.
## Syntax
```
Remove-AcctADAccount [-IdentityPoolName] <String> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-RemovalOption <ADIdentityRemoveAccountOption>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AcctADAccount [-IdentityPoolName] <String> -ADAccountSid <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-RemovalOption <ADIdentityRemoveAccountOption>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AcctADAccount -IdentityPoolUid <Guid> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-RemovalOption <ADIdentityRemoveAccountOption>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AcctADAccount -IdentityPoolUid <Guid> -ADAccountSid <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-RemovalOption <ADIdentityRemoveAccountOption>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to remove AD accounts from an identity pool.  This removes the AD account from the Citrix service management scope.  This process provides the options for removing the account in AD (or disabling it) if required.

All aspects of this command that need to make modifications to the accounts in AD will use the account that the runspace is using.  This means that if an account is to be removed from AD or disabled, the user performing the operation in PowerShell must have sufficient privileges in AD for this operation to complete successfully.

If the option to remove the account from AD or to disable it in AD is specified, the AD operation must succeed for the account to be removed from the Citrix AD Identity Service database. Use caution when using the Force parameter because this allows removal of accounts that are in the 'inUse' state, which may result in the machines becoming unusable.


## Related Commands

* [New-AcctADAccount](./New-AcctADAccount/)
* [Add-AcctADAccount](./Add-AcctADAccount/)
* [Repair-AcctADAccount](./Repair-AcctADAccount/)
* [Unlock-AcctADAccount](./Unlock-AcctADAccount/)
* [Update-AcctADAccount](./Update-AcctADAccount/)
* [Get-AcctADAccount](./Get-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The identity pool that the accounts are to be removed from. | true | false |  |
| ADAccountName | The AD account name to be removed. AD accounts are accepted in the following formats: Fully qualified DN e.g. CN=MyComputer,OU=Computers,DC=MyDomain,DC=Com; UPN format e.g MyComputer@MyDomain.Com; Domain qualified e.g MyDomain\\MyComputer. | true | false |  |
| ADAccountSid | The Active Directory Account SID for the account to be removed. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool that the accounts are to be removed from. | true | true (ByPropertyName) |  |
| ADUserName | The username for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| ADPassword | The matching password for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| RemovalOption | Defines the behavior relating to the AD account.<br>None - Do not attempt to remove the account from AD Delete - Attempt to remove the account from AD Disable - Attempt to disable the account in AD | false | false | None |
| Force | Indicates if accounts that are marked as 'in-use' can be removed. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Accountoperationsummary
The remove-AcctADAccout command returns an object with the following parameters;<br>    SuccessfulAccountsCount &lt;int&gt;<br>        The number of accounts that were removed successfully.<br>    FailedAccountsCount &lt;int&gt;<br>        The number of accounts that were not removed.<br>    FailedAccounts &lt;Citrix.ADIdentity.Sdk.AccountError\[\]&gt;<br>        The list of accounts that failed to be removed.  Each one has the following parameters:<br>            ADAccountName &lt;string&gt;<br>            ADAccountSid &lt;String&gt;<br>            ErrorReason &lt;ADIdentityStatus&gt;<br>               This can be one of the following<br>                   UnableToConvertDomain<br>                   IdentityNotLocatedInDomain<br>                   IdentityNotInIdentityPool<br>                   IdentityObjectInUse<br>                   IdentityObjectLocked<br>                   ADServiceDatabaseError<br>                   ADServiceDatabaseNotConfigured<br>                   ADServiceStatusInvalidDb<br>                   FailedToConnectToDomainController<br>                   FailedToDisableAccountInAD<br>                   FailedToDeleteAccountInAD<br>                   FailedToExecuteSearchInAD<br>                   FailedToAccessComputerAccountInAD<br>            DiagnosticInformtion &lt;Exception&gt;<br>              Any other error information
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    IdentityPoolNotFound<br>    The specified identity pool was not found.<br>    IdentityPoolAlreadyLocked<br>    The specified identity pool was locked by another operation.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -ADAccountName "Domain\account","domain\account2"

    SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

    -----------------------       -------------------    --------------

                          2                         0    {}
```
#### Description
Removes two accounts (account and account2) from the identity pool called "MyPool", leaving the AD accounts untouched.
### Example 2
```
C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -RemovalOption Delete -ADAccountName "Domain\account","domain\account2"

    SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

    -----------------------       -------------------    --------------

                          2                         0    {}
```
#### Description
Removes two accounts (account and account2) from the identity pool called "MyPool" (and from Active Directory).
### Example 3
```
C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -ADAccountName "Domain\account","domain\account2" -Force

    SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

    -----------------------       -------------------    --------------

                          2                         0    {}
```
#### Description
Removes two accounts (account and account2) from the identity pool called "MyPool", leaving the AD accounts untouched. The accounts are removed regardless of whether they are in the 'inUse' state or not.
### Example 4
```
C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -ADAccountName "Domain\account","domain\account2" -OutVariable result

    SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

    -----------------------       -------------------    --------------

    1                                               1    {account2}

    C:\PS>$result[0].FailedAccounts

    ADAccountName                 ADAccountSid           ErrorReason

    -------------                 -------------          ------------

    Domain\account2               account2               IdentityObjectLocked
```
#### Description
Shows failure of removal of one of two accounts and how to retrieve the failure reason.
### Example 5
```
C:\PS>Remove-AcctADAccount -IdentityPoolName MyPool -ADAccountSid S-1-5-21-1315084875-1285793635-2418178940-2685

    SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

    -----------------------       -------------------    --------------

    1                                               0    {}
```
#### Description
Removes one account (S-1-5-21-1315084875-1285793635-2418178940-2685) from the identity pool called "MyPool", leaving the AD accounts untouched.
