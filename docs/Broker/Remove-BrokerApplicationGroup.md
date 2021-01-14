
# Remove-Brokerapplicationgroup
Remove application groups from the system, or break the association between an application group and a desktop group.
## Syntax
```
Remove-BrokerApplicationGroup [-InputObject] <ApplicationGroup[]> [-Force] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerApplicationGroup [-Name] <String> [-Force] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet has 2 functions:

* Break associations between application groups and desktop groups.
* Remove application groups from the system.

Associating an application group with a desktop group allows the applications that are members of that application group to be launched on machines that are members of the associated desktop group. Breaking that association means that those applications may no longer be launched on those machines.

To remove an application group from the system, you must first remove all of its applications. Use the Remove-BrokerApplication cmdlet to remove an application (either to remove it from an application group, or to remove it from the system entirely).


## Related Commands

* [Add-BrokerApplicationGroup](./Add-BrokerApplicationGroup/)
* [Get-BrokerApplicationGroup](./Get-BrokerApplicationGroup/)
* [New-BrokerApplicationGroup](./New-BrokerApplicationGroup/)
* [Rename-BrokerApplicationGroup](./Rename-BrokerApplicationGroup/)
* [Set-BrokerApplicationGroup](./Set-BrokerApplicationGroup/)
* [Remove-BrokerApplication](./Remove-BrokerApplication/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the application groups to remove. | true | true (ByValue) |  |
| Name | Removes application groups whose name matches the given pattern. | true | true (ByPropertyName) |  |
| Force | When this flag is specified, an application group may be removed from the system even if its SessionSharingEnabled property is false and one of its applications is still running in some session.<br>Such an application group cannot by default be removed, because doing so would allow for other applications to be launched into existing sessions. Either wait until the sessions associated with the application group have exited, or use the -Force flag. | false | false |  |
| DesktopGroup | When this parameter is specified, the application groups are removed from the given desktop group. The desktop group may be specified either by its Uid or by its name.<br>When this parmeter is not specified, the application groups are removed from the system entirely. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Applicationgroup
You can pipe application groups to Remove-BrokerApplicationGroup.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerApplicationGroup Office -DesktopGroup Windows10VDAs
```
#### Description
Remove the association between the 'Office' application group and the 'Windows10VDAs' desktop group. The 'Office' applications will no longer be launchable on the machines in the 'Windows10VDAs' desktop group.
### Example 2
```
C:\PS> Remove-BrokerApplicationGroup Office
```
#### Description
Remove the 'Office' application group from the system altogether. You must remove all applications from the application group first.
