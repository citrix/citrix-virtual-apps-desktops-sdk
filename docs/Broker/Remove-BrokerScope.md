
# Remove-Brokerscope
Remove the specified catalog/desktop group from the given scope(s).
## Syntax
```
Remove-BrokerScope [-InputObject] <Scope[]> [-ApplicationGroup <ApplicationGroup>] [-Catalog <Catalog>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerScope cmdlet is used to remove a scopeable object object from the given scope(s). A scopeable object is one of:

* a catalog
* a desktop group
* an application group

To remove a scopeable object from a scope you need permission to change the scopes of the scopeable object.

If the scopeable object is not in a specified scope, that scope will be silently ignored.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the scopes to remove the object from. | true | true (ByValue) | null |
| ApplicationGroup | Specifies the application group object to be removed. | false | true (ByValue) |  |
| Catalog | Specifies the catalog object to be removed. | false | true (ByValue) |  |
| DesktopGroup | Specifies the desktop group object to be removed. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Scope
You can pipe scopes to Remove-BrokerScope.
## Return Values

### 

## Examples

### Example 1
```
C:\PS> Remove-BrokerScope Sales,Marketing -DesktopGroup "Win7 Desktops"
```
#### Description
Removes the "Win7 Desktops" desktop group from both the Sales and Marketing scopes.
### Example 2
```
C:\PS> Sales,Marketing | Remove-BrokerScope -DesktopGroup 'Win7 Desktops'
```
#### Description
Removes the "Win7 Desktops" desktop group from both the Sales and Marketing scopes.
