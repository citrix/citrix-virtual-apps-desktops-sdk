
# Export-Acctidentitypool
Exports a Identity Pool
## Syntax
```
Export-AcctIdentityPool [-IdentityPoolName] <String> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Export-AcctIdentityPool -IdentityPoolUid <Guid> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Export an Identity pool and it ADAccounts to JSON encoded string, note that any account that has been created by has not yet been used by MCS will not be exported


## Related Commands

* [Import-AcctIdentityPool](./Import-AcctIdentityPool/)
* [Export-ProvScheme](./Export-ProvScheme/)
* [Import-ProvScheme](./Import-ProvScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool. | true | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.String
A JSON encoded version of the identity pool and the ADAccounts that are part of the identity pool
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
Export-AcctIdentityPool -IdentityPoolName MyIdentityPool
```
#### Description
Exports the Identity pool MyIdentityPool
