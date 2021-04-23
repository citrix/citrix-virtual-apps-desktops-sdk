
# Remove-Brokerconfigurationslot
Removes a configuration slot.
## Syntax
```
Remove-BrokerConfigurationSlot [-InputObject] <ConfigurationSlot[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerConfigurationSlot [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Removes a configuration slot from the site. All machine configurations associated with this slot are also removed.


## Related Commands

* [New-BrokerConfigurationSlot](./New-BrokerConfigurationSlot/)
* [Get-BrokerConfigurationSlot](./Get-BrokerConfigurationSlot/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Configuration slot to remove. | true | true (ByValue) |  |
| Name | Name of configuration slot to remove. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Configuration Slot To Remove
Configuration slots may be specified through pipeline input.
## Return Values

### None

## Examples

### Example 1
```
Remove-BrokerConfigurationSlot -Name "User Profile Manager"
```
#### Description
Remove the configuration slot named "User Profile Manager".
