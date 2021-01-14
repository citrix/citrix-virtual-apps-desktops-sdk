
# Add-Brokerapplicationgroup
Adds application groups to a desktop group.
## Syntax
```
Add-BrokerApplicationGroup [-InputObject] <ApplicationGroup[]> [-DesktopGroup <DesktopGroup>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Add-BrokerApplicationGroup [-Name] <String> [-DesktopGroup <DesktopGroup>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Add-BrokerApplicationGroup cmdlet is used to associate one or more application groups with an existing desktop group.

Associating an application group with a desktop group makes the desktop groups's machines available for launching applications in that application group. Until an application group is associated with a desktop group, its applications cannot be launched.

There are two parameter sets for this cmdlet, allowing you to specify the application groups either by Name or by an array of object references. Uids can also be substituted for the object references.

See about\_Broker\_Applications for more information.


## Related Commands

* [Get-BrokerApplicationGroup](./Get-BrokerApplicationGroup/)
* [New-BrokerApplicationGroup](./New-BrokerApplicationGroup/)
* [Remove-BrokerApplicationGroup](./Remove-BrokerApplicationGroup/)
* [Rename-BrokerApplicationGroup](./Rename-BrokerApplicationGroup/)
* [Set-BrokerApplicationGroup](./Set-BrokerApplicationGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the application group to associate with the desktop group. Its Uid can also be substituted for the object reference. | true | true (ByValue) |  |
| Name | Specifies the name of the application group to associate with the desktop group. | true | true (ByPropertyName) |  |
| DesktopGroup | Specifies the desktop groups with which the application groups should be associated.<br>Note that application groups can only be associated with desktop groups whose delivery type is either AppsOnly or DesktopsAndApps. | false | true (ByValue) |  |
| Priority | Specifies the priority of the mapping between the application group and desktop group. Lower numbers imply higher priority with zero being highest.<br>If one association has a higher priority than the other, machines from that group will be selected for launching sessions until all machines are at maximum load, in maintenance mode, unregistered, or unavailable for any other reason. Only when all machines from the higher-priority desktop group are unavailable will new connections be routed to the next lowest priority desktop group.<br>If multiple associations with equal priorities are encountered, session launches will be load balanced across all machines in both desktop groups. The least-loaded machine across the desktop groups will be chosen. | false | true (ByPropertyName) | 0 |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Applicationgroup, Or As Appropriate By Property Name
You can pipe the application group to be added to Add-BrokerApplicationGroup. You can also pipe some of the other parameters by name.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Add-BrokerApplicationGroup -Name "Office Apps" -DesktopGroup "Private DesktopGroup"
```
#### Description
Adds the application group with the Name "Office Apps" to the desktop group called "Private DesktopGroup".
