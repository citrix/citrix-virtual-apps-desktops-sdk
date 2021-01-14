
# Remove-Brokericon
Remove an icon.
## Syntax
```
Remove-BrokerIcon [-InputObject] <Icon[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Removes an icon from the database.


## Related Commands

* [Get-BrokerIcon](./Get-BrokerIcon/)
* [New-BrokerIcon](./New-BrokerIcon/)
* [Set-BrokerIconMetadata](./Set-BrokerIconMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the icon to remove. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Icon
The icon to be removed can be piped into the cmdlet.
## Return Values

### None

## Notes
Note that if the icon is currently in use, for example, as a desktop icon, it cannot be removed until the association is cleared.
## Examples

### Example 1
```
C:\PS> Remove-BrokerIcon 3
```
#### Description
Removes the icon with Uid 3.
