
# Add-Brokerapplication
Adds applications to a desktop group or application group.
## Syntax
```
Add-BrokerApplication [-InputObject] <Application[]> [-ApplicationGroup <ApplicationGroup>] [-DesktopGroup <DesktopGroup>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Add-BrokerApplication [-Name] <String> [-ApplicationGroup <ApplicationGroup>] [-DesktopGroup <DesktopGroup>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Add-BrokerApplication cmdlet is used to associate one or more applications with an existing desktop group or application group.

There are two parameter sets for this cmdlet, allowing you to specify the application either by its BrowserName or by an array of object references. Uids can also be substituted for the object references.

See about\_Broker\_Desktops and about\_Broker\_Applications for more information.


## Related Commands

* [New-BrokerApplication](./New-BrokerApplication/)
* [Add-BrokerApplication](./Add-BrokerApplication/)
* [Add-BrokerTag](./Add-BrokerTag/)
* [Remove-BrokerApplication](./Remove-BrokerApplication/)
* [Rename-BrokerApplication](./Rename-BrokerApplication/)
* [Move-BrokerApplication](./Move-BrokerApplication/)
* [Set-BrokerApplication](./Set-BrokerApplication/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the application to associate. Its Uid can also be substituted for the object reference. | true | true (ByValue) |  |
| Name | Specifies the name of the application to be associated with the desktop group. | true | true (ByPropertyName) |  |
| ApplicationGroup | Specifies which application group this application should be associated with. | false | true (ByValue) |  |
| DesktopGroup | Specifies which desktop group this application should be associated with. Note that applications can only be associated with desktop groups of the AppsOnly or DesktopsAndApps delivery type. | false | true (ByValue) |  |
| Priority | Specifies the priority of the mapping between the application and desktop group where lower numbers imply higher priority with zero being highest.<br>If one association has a higher priority than the other, machines from that group will be selected for launching sessions until all machines are at maximum load, in maintenance mode, unregistered, or unavailable for any other reason. Only when all machines from the higher-priority group are unavailable will new connections be routed to the next lowest priority group.<br>If multiple associations with equal priorities are encountered, session launches will be load balanced across all machines in both groups. The least-loaded machine across the groups will be chosen.<br>This parameter is used only when adding an application to a desktop group. It is an error to specify a priority when adding an application to an application group. | false | true (ByPropertyName) | 0 |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Application, Or As Appropriate By Property Name
You can pipe the application to be added to Add-BrokerApplication. You can also pipe some of the other parameters by name.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Add-BrokerApplication -Name "Notepad" -DesktopGroup "Private DesktopGroup"
```
#### Description
Adds the application with a Name of "Notepad" to the desktop group called "Private DesktopGroup".
