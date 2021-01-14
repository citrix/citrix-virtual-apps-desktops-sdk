
# Remove-Hyphypervisorconnectionaddress
Removes addresses from the list of available connection addresses.
## Syntax
```
Remove-HypHypervisorConnectionAddress [-LiteralPath] <String> [-HypervisorAddress] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to remove addresses that can be used to connect to the hypervisor specified by the hypervisor connection.  If all addresses are removed, the connection cannot be used until a valid address is added to the hypervisor connection.


## Related Commands

* [Add-HypHypervisorConnectionAddress](./Add-HypHypervisorConnectionAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a Host Service provider to the hosting unit item to which to add the address. The path specified must be in one of the following formats: &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt; or  &lt;drive&gt;:\\HostingUnits\\{HostingUnit Uid&gt;} | true | false |  |
| HypervisorAddress | Specifies the address to be removed.  If this parameter is not provided, all addresses are removed from the hypervisor connection. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String<br>    You Can Pipe A String That Contains A Path To Remove-Hyphypervisorconnectionaddress (Path Parameter).

## Return Values

### 

## Notes
Changes to a hypervisor connection affect all entities that reference the connection. If all addresses are removed from the connection, any other entities that reference the hypervisor connection (e.g. hosting units) cannot make new connections to the hypervisor.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    InputConnectionsPathInvalid<br>    The path provided is not to an item in a subdirectory of a hosting unit item.<br>    HypervisorConnectionAddressForeignKeyObjectDoesNotExist<br>    The hypervisor connection to which the address is to be added could not be located.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Remove-HypHypervisorConnectionAddress -LiteralPath XDHyp:\HostingUnits\MyHypervisorConnection -HypervisorAddress 'http:\\myserver.com'
```
#### Description
The command removes the address "http:\\\\myserver.com" from the hypervisor connection called "MyHypervisorConnection".
### Example 2
```
c:\PS>Get-Item –Path XDHYP:\Connections\\* | Remove-HypHypervisorConnectionAddress
```
#### Description
The command removes all addresses from all the hypervisor connections currently defined.
