
# Rename-Acctidentitypool
Renames an identity pool.
## Syntax
```
Rename-AcctIdentityPool [-IdentityPoolName] <String> [-NewIdentityPoolName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Rename-AcctIdentityPool -IdentityPoolUid <Guid> -NewIdentityPoolName <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to change the name of an existing identity pool.


## Related Commands

* [Get-AcctIdentityPool](./Get-AcctIdentityPool/)
* [Set-AcctIdentityPool](./Set-AcctIdentityPool/)
* [Remove-AcctIdentityPool](./Remove-AcctIdentityPool/)
* [Test-AcctIdentityPoolNameAvailable](./Test-AcctIdentityPoolNameAvailable/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool to be renamed. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool to be renamed. | true | false |  |
| NewIdentityPoolName | The new name for the identity pool.  This must be a name which is not used by an existing identity pool, and it must not contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | true (ByPropertyName) |  |
| PassThru | Defines whether or not the command returns a result showing the new state of the updated provisioning scheme. | false | true (ByPropertyName) | true |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Identitypool
This object provides details of the identity pool and contains the following information:<br>IdentityPoolName &lt;string&gt;<br>    The name of the identity pool.<br>IdentityPoolUid &lt;Guid&gt;<br>    The unique identifier for the identity pool.<br>NamingScheme &lt;string&gt;<br>    The naming scheme for the identity pool.<br>NamingSchemeType &lt;Citrix.XDInterServiceTypes.ADIdentityNamingScheme&gt;<br>    The naming scheme type for the identity pool. This can be one of the following:<br>        Numeric - naming scheme uses numeric indexes<br>        Alphabetic - naming scheme uses alphabetic indexes<br>StartCount &lt;int&gt;<br>    The next index to be used when creating an identity from the identity pool.<br>OU &lt;string&gt;<br>    The Active Directory distinguished name for the OU in which accounts created from this identity pool will be created.<br>Domain &lt;string&gt;<br>    The Active Directory domain that accounts in the pool belong to.<br>Lock &lt;Boolean&gt;<br>    Indicates if the identity pool is locked.
## Notes
In the case of failure the following errors can result.<br>    Error Codes<br>    -----------<br>    IdentityPoolObjectNotFound<br>    The specified identity pool could not be located.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Rename-AcctIdentityPool -IdentityPoolName oldName -NewIdentityPoolName newName
```
#### Description
Renames an existing identity pool called "oldName" to be called "newName".
