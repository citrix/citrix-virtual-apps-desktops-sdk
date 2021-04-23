
# Unlock-Acctidentitypool
Unlocks identity pools.
## Syntax
```
Unlock-AcctIdentityPool [-IdentityPoolName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Unlock-AcctIdentityPool -IdentityPoolUid <Guid> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to unlock the specified identity pool.  Identity pools are locked automatically when being updated (e.g. when new accounts are being created into them).  The pool must never be left in a locked state; this command allows recovery from an error should this ever occur.  Use this command with caution, as unlocking an identity pool which is supposed to be locked may result in unexpected behavior.


## Related Commands

* [New-AcctIdentityPool](./New-AcctIdentityPool/)
* [Remove-AcctIdentityPool](./Remove-AcctIdentityPool/)
* [Set-AcctIdentityPool](./Set-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool to unlock. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool to be unlocked. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Adidentity.Sdk.Identitypool<br>    You Can Pipe An Object Containing A Parameter Called 'Identitypoolname' To Unlock-Acctidentitypool.

## Return Values

### 

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    IdentityPollObjectNotFound<br>    The specified identity pool could not be located.<br>    IdentityPoolAlreadyUnlocked<br>    The specified identity pool is not locked.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Unlock-AcctIdentityPool -IdentityPool MyPool
```
#### Description
Unlocks the identity pool called "MyPool".
### Example 2
```
C:\PS>Get-AcctIdentityPool -Filter {Lock -eq $true} | Unlock-AcctIdentityPool
```
#### Description
Unlocks all the locked identity pools.
