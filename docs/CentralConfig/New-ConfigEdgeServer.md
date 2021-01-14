
# New-Configedgeserver
Creates a new edge server object
## Syntax
```
New-ConfigEdgeServer [-Name] <String> -MachineAddress <String> -Sid <String> -Uuid <Guid> [-Description <String>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
New-ConfigEdgeServer cmdlet creates a new edge server object.

An edge server is a machine which is running an agent service that performs a number of duties; these agent services are largely stateless and communicate back to the Citrix Workspace Cloud components in the cloud.


## Related Commands

* [Get-ConfigEdgeServer](./Get-ConfigEdgeServer/)
* [Set-ConfigEdgeServer](./Set-ConfigEdgeServer/)
* [Rename-ConfigEdgeServer](./Rename-ConfigEdgeServer/)
* [Remove-ConfigEdgeServer](./Remove-ConfigEdgeServer/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies a name for the edge server. Each edge server must have a unique name. | true | true (ByPropertyName) |  |
| MachineAddress | The address used when contacted by local components such as VDAs | true | true (ByPropertyName) |  |
| Sid | The Security Identifier value in tenant AD domain | true | true (ByPropertyName) |  |
| Uuid | The uuid used when being contacted from cloud components such as controllers | true | true (ByPropertyName) |  |
| Description | Optional value to specify a description for the edge server | false | true (ByPropertyName) |  |
| ZoneUid | Specifies the Zone affinity for the edge server | false | true (ByPropertyName) | If no value is provided the edge server is placed in the Primary zone |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Configuration.Sdk.Edgeserver
The newly created edge server
## Examples

### Example 1
```
C:\PS> New-ConfigEdgeServer W2K12R2 -MachineAddress "EdgeSrv.address.com" -Sid 21-3623811015-3361044348-30300820
```
#### Description
This command creates an edge server
