
# Import-Acctidentitypool
Imports a Identity Pool in the site
## Syntax
```
Import-AcctIdentityPool -IdentityPoolData <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Imports a Identity Pool from another site, that has been exported using the Export-IdentityPool


## Related Commands

* [Export-AcctIdentityPool](./Export-AcctIdentityPool/)
* [Export-ProvScheme](./Export-ProvScheme/)
* [Import-ProvScheme](./Import-ProvScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolData | The Json encoded data | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.String
The Json encoded string
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
Import-IdentityPool -IdentityPoolData $identityPoolData
```
#### Description
Import the identityPool definded in the variable \$identityPoolData
