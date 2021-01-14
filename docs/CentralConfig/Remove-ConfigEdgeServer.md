
# Remove-Configedgeserver
Removes edge servers from the site
## Syntax
```
Remove-ConfigEdgeServer [-InputObject] <EdgeServer[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ConfigEdgeServer [-Uid] <Guid[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ConfigEdgeServer [-Name] <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Remove edge servers from the site


## Related Commands

* [Get-ConfigEdgeServer](./Get-ConfigEdgeServer/)
* [New-ConfigEdgeServer](./New-ConfigEdgeServer/)
* [Set-ConfigEdgeServer](./Set-ConfigEdgeServer/)
* [Rename-ConfigEdgeServer](./Rename-ConfigEdgeServer/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the edge server objects to delete | true | true (ByValue) |  |
| Uid | Specifies the UID of the edge server to delete | true | true (ByPropertyName) |  |
| Name | Specifies the name of the edge server to delete | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Configuration.Sdk.Edgeserver
You can pipe the edge servers to be deleted to Remove-ConfigEdgeServer.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-ConfigEdgeServer -Name W2K12R1
```
#### Description
Removes an edge server with the specified name
### Example 2
```
C:\PS> Get-ConfigEdgeServer -ZoneName Secondary | Remove-ConfigEdgeServer
```
#### Description
Removes all edge servers from the zone named Secondary
