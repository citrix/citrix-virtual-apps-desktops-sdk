
# Add-Brokerscope
Add the specified catalog/desktop group to the given scope(s).
## Syntax
```
Add-BrokerScope [-InputObject] <Scope[]> [-ApplicationGroup <ApplicationGroup>] [-Catalog <Catalog>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Add-BrokerScope cmdlet is used to associate a scopeable object with the given scope(s). A scopeable object is one of:

* a catalog
* a desktop group
* an application group

To add a scopeable object to a scope you need permission to change the scopes of the scopeable object and permission to add objects to all of the scopes you have specified.

If the scopeable object is already in any scope supplied, that scope will be silently ignored.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the scope(s) to add the object to. Each can take the form of either the string form of the scope's GUID or its name. | true | true (ByValue) |  |
| ApplicationGroup | Specifies the application group to be added. This can take the form of an existing application group object, an application group Uid or name. | false | true (ByValue) |  |
| Catalog | Specifies the catalog object to be added. This can take the form of an existing catalog object, a catalog Uid or name. | false | true (ByValue) |  |
| DesktopGroup | Specifies the desktop group object to be added. This can take the form of an existing desktop group object, a desktop group Uid or name. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Scope
You can pipe scopes to Add-BrokerScope.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Add-BrokerScope Sales –DesktopGroup 27
```
#### Description
Adds the desktop group with Uid 27 to the Sales scope.
### Example 2
```
C:\PS> Add-BrokerScope BFC74867-C6EF-482C-996F-3E0D340E96AC -Catalog BangaloreMachines
```
#### Description
Adds the BangaloreMachines catalog to the scope with the specified ScopeID.
