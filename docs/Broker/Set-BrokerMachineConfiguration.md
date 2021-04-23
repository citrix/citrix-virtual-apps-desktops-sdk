
# Set-Brokermachineconfiguration
Sets the properties of a machine configuration.
## Syntax
```
Set-BrokerMachineConfiguration [-InputObject] <MachineConfiguration[]> [-PassThru] [-Description <String>] [-Policy <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerMachineConfiguration [-Name] <String> [-PassThru] [-Description <String>] [-Policy <Byte[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Sets the properties of a machine configuration. The encoded settings data must only contain settings that match the SettingsGroup of the associated configuration slot. Use the SDK snap-in that matches the SettingsGroup of the associated configuration slot to generate new encoded settings data or modify existing settings values.


## Related Commands

* [New-BrokerMachineConfiguration](./New-BrokerMachineConfiguration/)
* [Get-BrokerMachineConfiguration](./Get-BrokerMachineConfiguration/)
* [Rename-BrokerMachineConfiguration](./Rename-BrokerMachineConfiguration/)
* [Remove-BrokerMachineConfiguration](./Remove-BrokerMachineConfiguration/)
* [Add-BrokerMachineConfiguration](./Add-BrokerMachineConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Machine configuration to modify. | true | true (ByValue) |  |
| Name | Name of machine configuration to modify. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Description | New description for the machine configuration. | false | false |  |
| Policy | New binary array of encoded settings data. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Machineconfiguration
Machine configuration to modify.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Machineconfiguration
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.MachineConfiguration object.
## Examples

### Example 1
```
Set-BrokerMachineConfiguration -Name "UPM\Finance Department" -Policy $newPolicy
```
#### Description
Use the encoded settings binary data in \$newPolicy to update the machine configuration.
### Example 2
```
Get-BrokerMachineConfiguration -Name "UPM\\*" | Set-BrokerMachineConfiguration -Description "User Profile Management"
```
#### Description
Assign the description "User Profile Management" to every machine configuration associated with the UPM slot.
