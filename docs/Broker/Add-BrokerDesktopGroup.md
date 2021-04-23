
# Add-Brokerdesktopgroup
Associate Remote PC desktop groups with the specified Remote PC catalog.
## Syntax
```
Add-BrokerDesktopGroup [-InputObject] <DesktopGroup[]> [-RemotePCCatalog <Catalog>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Add-BrokerDesktopGroup [-Name] <String> [-RemotePCCatalog <Catalog>] [-Priority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet forms relationships between Remote PC desktop groups and catalogs.

The Remote PC relationships are used by Remote PC automation to determine which desktop groups a machine in a particular Remote PC catalog can be published to. The assignment policy rules belonging to those desktop groups also determines the set of users that are allowed to be assigned to machines from the catalog.


## Related Commands

* [Remove-BrokerDesktopGroup](./Remove-BrokerDesktopGroup/)
* [Add-BrokerCatalog](./Add-BrokerCatalog/)
* [Remove-BrokerCatalog](./Remove-BrokerCatalog/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies one or more Remote PC desktop groups to add to a Remote PC catalog. | true | true (ByValue) |  |
| Name | Specifies the Remote PC desktop groups to add to a Remote PC catalog based on their name properties. | true | true (ByPropertyName) |  |
| RemotePCCatalog | The Remote PC catalog which the desktop groups are to be added to. Specified by name, Uid or instance. | false | true (ByValue) |  |
| Priority | Desktop group to catalog associations carry a priority number, where numerically lower values indicate a higher priority.<br>The priority relative to other associations determines which desktop group Remote PC automation will move a qualifying unconfigured machine into when it registers. Priority also determines which desktop group a machine will be published to when a user is assigned to the machine by Remote PC automation.<br>If a value is not supplied, then the desktop group association is automatically assigned a lower priority than any existing associations.<br>If a priority value is specified that conflicts with an existing association's priority value, then the new association is inserted with that value and existing associations are renumbered upwards to accommodate it. | false | true (ByPropertyName) | See description |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Desktopgroup
The set of Remote PC desktop groups to be added to the catalog can be piped into this cmdlet.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Get-BrokerDesktopGroup -IsRemotePC $true | Add-BrokerDesktopGroup -RemotePCCatalog 42
```
#### Description
Add all Remote PC desktop groups to Remote PC catalog 42.
### Example 2
```
C:\PS> Add-BrokerDesktopGroup -Name \*MyGroup\* -RemotePCCatalog RPCCat
```
#### Description
Add desktop groups with names containing MyGroup to Remote PC catalog with name "RPCCat".
