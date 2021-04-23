
# Remove-Hyphostingunitnetwork
Removes networks from a hosting unit.
## Syntax
```
Remove-HypHostingUnitNetwork [-LiteralPath] <String> [-NetworkPath] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to remove networks from a hosting unit. This does not remove the network from the hypervisor, only the reference to the network for the Host Service. After it is removed, the network is no longer available for associating with virtual NICs (when creating new virtual machines with the Machine Creation Service). Any virtual machines that have been created already continue to use the network until they are removed from the deployment. This command cannot be used if the connection for the hosting unit is in maintenance mode. If the network to be removed no longer exists on the hypervisor for the hosting unit, you must supply a fully qualified path to the network location.


## Related Commands

* [Add-HypHostingUnitNetwork](./Add-HypHostingUnitNetwork/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath |  | true | false |  |
| NetworkPath | Specifies the path in the hosting unit provider of the network to remove. The path specified must be in one of the following formats: &lt;drive&gt;:\\Connections\\&lt;HostingUnitName&gt;\\MyNetwork.network or  &lt;drive&gt;:\\Connections\\{&lt;hostingUnit Uid&gt;}\\MyNetwork.network | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. This can be a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String<br>    You Can Pipe A String That Contains A Path To Remove-Hyphostingunitnetwork (Path Parameter).

## Return Values

### 

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    HostingUnitsPathInvalid<br>    The path provided is not to an item in a subdirectory of a hosting unit item.<br>    HostingUnitNetworkObjectToDeleteDoesNotExist<br>    The network path specified is not part of the hosting unit.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Remove-HypHostingUnitNetwork -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -NetworkPath 'XDHyp:\HostingUnits\MyHostingUnits\newNetwork.network'
```
#### Description
The command removes the network called "newNetwork.network" from the hosting unit called "MyHostingUnit"
