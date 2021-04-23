
# Update-Hyphypervisorconnection
Requests the host service to update the connection properties that depend on the version of hypervisor in use.
## Syntax
```
Update-HypHypervisorConnection [-LiteralPath] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to update the version-specific properties of a hypervisor connection, after an upgrade to the hypervisor system which may provide new capabilities.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a Host Service provider to the hypervisor connection item to be updated. The path specified must be in one of the following formats; &lt;drive&gt;:\\Connections\\&lt;HypervisorConnectionName&gt; or  &lt;drive&gt;:\\Connections\\{HypervisorConnection Uid&gt;} | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in will connect to.  This can be provided as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### 

## Return Values

### 

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    InvalidPath<br>    The path provided is not in the required format.<br>    HypervisorInMaintenanceMode<br>    The hypervisor is in maintenance mode and cannot be updated.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Update-HypHypervisorConnection -LiteralPath xdhyp:\connections\Connection1
```
#### Description
This command requests that the properties of Connection1 be updated to match the current capabilities of the hypervisor.
