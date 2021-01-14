
# Update-Acctadaccount
Refreshes the AD computer account state stored in the AD Identity Service.
## Syntax
```
Update-AcctADAccount [-IdentityPoolName] <String> [-AllAccounts] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Update-AcctADAccount -IdentityPoolUid <Guid> [-AllAccounts] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to synchronize the state of the AD accounts stored in the AD Identity Service with the AD accounts themselves.  By default, this checks all accounts marked as 'error' to determine if accounts are still in an error state (i.e. disabled or locked).  If you specify the 'AllAccounts' option, it checks accounts not in error state and updates the status of these accounts too.


## Related Commands

* [New-AcctADAccount](./New-AcctADAccount/)
* [Add-AcctADAccount](./Add-AcctADAccount/)
* [Remove-AcctADAccount](./Remove-AcctADAccount/)
* [Repair-AcctADAccount](./Repair-AcctADAccount/)
* [Unlock-AcctADAccount](./Unlock-AcctADAccount/)
* [Get-AcctADAccount](./Get-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool for the accounts to be refreshed. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool of the AD accounts that are to be refreshed. | true | false |  |
| AllAccounts | Indicates if all accounts should be refreshed or only the ones marked as in error. | false | false | false |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Update-AcctADAccount -IdentityPoolName MyPool
```
#### Description
Checks the status of all accounts in the Identity Pool MyPool that are currently mark as in the Error state and checks if the account is now available.
### Example 2
```
c:\PS>Update-AcctADAccount -IdentityPoolName MyPool -AllAccounts
```
#### Description
Checks the status of all accounts in the Identity Pool MyPool marking them as Available, InUse, Tainted or Error as appropriate.
