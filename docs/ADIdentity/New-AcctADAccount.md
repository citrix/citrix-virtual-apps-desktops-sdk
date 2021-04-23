
# New-Acctadaccount
Creates AD computer accounts in the specified identity pool.
## Syntax
```
New-AcctADAccount [-IdentityPoolName] <String> -Count <Int32> [-StartCount <Int32>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AcctADAccount [-IdentityPoolName] <String> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AcctADAccount -IdentityPoolUid <Guid> -Count <Int32> [-StartCount <Int32>] [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AcctADAccount -IdentityPoolUid <Guid> -ADAccountName <String[]> [-ADUserName <String>] [-ADPassword <SecureString>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to create new AD computer accounts and register them in an already existing identity pool.

The accounts are created using the information stored in the identity pool. This provides the account name (via the Naming Scheme property and Start Count), domain, and OU.

The runspace used for this command must have sufficient privileges in Active Directory to create the new computer accounts.

The AD account names will pad the index to use all the space specified in the identity pool naming scheme (e.g. "acc###" will become "acc001"). However, if the index overflows the available space the cmdlet expands the format to use the next incremental number (e.g. "acc###" will become "acc1000" if the index is 10000, which cannot fit into the three '#' placeholders). If this expanded name exceeds the 15 character name limit, the accounts are not created.

There can be only one creation process running for a specific identity pool at any one time. Attempting to start another account creation process while an existing one is executing results in an error being returned.


## Related Commands

* [Add-AcctADAccount](./Add-AcctADAccount/)
* [Remove-AcctADAccount](./Remove-AcctADAccount/)
* [Get-AcctADAccount](./Get-AcctADAccount/)
* [Repair-AcctADAccount](./Repair-AcctADAccount/)
* [Unlock-AcctADAccount](./Unlock-AcctADAccount/)
* [Update-AcctADAccount](./Update-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool in which to create the accounts. | true | false |  |
| Count | The number of accounts to create. | true | false |  |
| ADAccountName | The AD account names to be created.  These are just the simple machine account names e.g. MyVM001 | true | false |  |
| IdentityPoolUid | The unique identifier for the identity pool in which the accounts will be created. | true | false |  |
| StartCount | The start index for the create process. | false | false |  |
| ADUserName | The username for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| ADPassword | The matching password for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Accountoperationdetailedsummary
The Add-AcctADAccount returns an object that contains the following parameters;<br>          SuccessfulAccountsCount &lt;int&gt;<br>            The number of accounts that were added successfully<br>          FailedAccountsCount &lt;int&gt;<br>            The number of accounts that were not added.<br>          FailedAccounts &lt;Citrix.ADIdentity.Sdk.AccountError\[\]&gt;<br>            The list of accounts that failed to be added.  Each one has the following parameters;<br>            ADAccountName &lt;string&gt;<br>            ADAccountSid &lt;String&gt;<br>            ErrorReason &lt;string&gt;<br>            This can be one of the following<br>              IdentityDuplicateObjectExists<br>                An identity with the same SID already exists.<br>              ADServiceDatabaseError<br>                  An error occurred in the service while attempting a database operation.<br>              ADServiceDatabaseNotConfigured<br>                  The operation could not be completed because the database for the service is not configured.<br>              ADServiceStatusInvalidDb<br>                  An error occurred in the service while attempting a database operation - communication with the database failed for<br>                  for various reasons.<br>              FailedToConnectToDomainController<br>                Contacting Active Directory failed.<br>              FailedToGetOrganizationUnitInAD<br>                Failed to access the OU in Active Directory.<br>              FailedToGetDefaultComputerContainerInAD<br>                Failed to access the default computers container in Active Directory.<br>              FailedToCreateComputerAccountInAD<br>                Failed to create the computer account in Active Directory.<br>              FailedToAccessComputerAccountInAD<br>                Failed to read the newly created computer account in Active Directory.<br>              FailedToGetSidFromAD<br>                Failed to get the SID for the created account from Active Directory.<br>              FailedToSetSamAccountNameInAD<br>                Failed to set the SAM account name in Active Directory for the account created.<br>              FailedToSetUserAccountControlInAD<br>                Failed to set the user account controller properties for the account created in Active Directory.<br>              FailedToSaveChangeInAD<br>                Failed to save the changes made to the created computer account in Active Directory.<br>              FailedToSetPasswordInAD<br>                Failed to set the password for the created computer account in Active Directory.<br>              FailedToEnableAccountInAD<br>                Failed to enable the newly created computer account in Active Directory.<br>              ComputerNameAlreadyInUseInAD<br>                The computer name for the computer to create is in use in Active Directory.<br>              FailedToGetDistinguishedNameInAD<br>                Failed to get the distinguished name for the created computer account in ActiveDirectory.<br>              FailedToSetDnsHostNameInAD<br>                Failed to set the Dns Host Name property for the created computer account in ActiveDirectory.<br>              FailedToSetDisplayNameInAD<br>                Failed to set the DisplayName property for the created computer account in ActiveDirectory.<br>              FailedToWriteServicePrincipalNameInAD<br>                Failed to set the ServicePrincipalName property for the created computer account in ActiveDirectory.<br>            DiagnosticInformtion &lt;Exception&gt;<br>              Any other error information<br>          SuccessfulAccounts &lt;Citrix.ADIdentity.Sdk.Identity\[\]&gt;<br>            The list of accounts that were successfully added.  Each object<br>            provides details of the identity and contains the following information:<br>            ADAccountSID &lt;string&gt;<br>                The Sid of the identity.<br>            ADAccountName &lt;string&gt;<br>                      The account name for the identity.<br>                      Domain &lt;string&gt;<br>                The domain name that the account was created in.<br>            State &lt;string&gt;<br>                The current state of the AD account. This can be one of the following:<br>                Error<br>                   The account is locked or disabled in AD.<br>                Available<br>                   The account is in AD and available to be consumed by the other Machine Creation Services.<br>                InUse<br>                   The account is in AD and is being consumed by the other Machine Creation Services.<br>                Tainted<br>                   The account is in AD and no longer consumed by other Machine Creation Services. However, the password is no longer known so cannot be reused without 'Repairing' the account.  See repair-AcctADAccount for details.<br>            Lock &lt;Boolean&gt;<br>                Indicates if the identity pool is locked.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    NamingSchemeNotSpecifiedForIdentityPool<br>    No naming scheme is defined in the specified identity pool.<br>    IdentityPoolObjectNotFound<br>    The specified identity pool was not located.<br>    IdentityPoolAlreadyLocked<br>    The specified identity pool is locked.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>New-AcctADAccount -IdentityPoolName MyPool -Count 2 -OutVariable result

          SuccessfulAccounts                SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

          ------------------                -----------------------       -------------------    --------------

          {MyDomain\ACC001, MyDomain\ACC002} 2                            0                      {}

          $result[0].SuccessfulAccounts

          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2684

          ADAccountName : MyDomain\ACC001

          Domain        : MyDomain.com

          State         : Available

          Lock          : False

          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2685

          ADAccountName : MyDomain\ACC002

          Domain        : MyDomain.com

          State         : Available

          Lock          : False
```
#### Description
Creates two new AD accounts and registers them in the identity pool called "MyPool".
### Example 2
```
c:\PS>New-AcctADAccount -IdentityPoolName MyPool -Count 2 -StartCount 50 -OutVariable result

          SuccessfulAccounts                SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

          ------------------                -----------------------       -------------------    --------------

          {MyDomain\ACC050, MyDomain\ACC051} 2                            0                      {}

          $result[0].SuccessfulAccounts

          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2686

          ADAccountName : MyDomain\ACC050

          Domain        : MyDomain.com

          State         : Available

          Lock          : False

          ADAccountSid  : S-1-5-21-1315084875-1285793635-2418178940-2687

          ADAccountName : MyDomain\ACC051

          Domain        : MyDomain.com

          State         : Available

          Lock          : False
```
#### Description
Creates two new AD accounts and registers them in the identity pool called "MyPool", starting from an index of 50.
