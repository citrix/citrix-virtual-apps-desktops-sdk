
# New-Brokermachineconfiguration
Creates a new machine configuration associated with an existing configuration slot.
## Syntax
```
New-BrokerMachineConfiguration -ConfigurationSlotUid <Int32> -LeafName <String> -Policy <Byte[]> [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Creates a new machine configuration containing settings that match the SettingsGroup of the associated configuration slot. This machine configuration can then be applied to a desktop group to have the settings applied to machines in that group.

The SettingsGroup of the configuration slot restricts the permitted settings. Use the SDK snap-in that matches the SettingsGroup to create the encoded settings data.


## Related Commands

* [Get-BrokerMachineConfiguration](./Get-BrokerMachineConfiguration/)
* [Set-BrokerMachineConfiguration](./Set-BrokerMachineConfiguration/)
* [Rename-BrokerMachineConfiguration](./Rename-BrokerMachineConfiguration/)
* [Remove-BrokerMachineConfiguration](./Remove-BrokerMachineConfiguration/)
* [Add-BrokerMachineConfiguration](./Add-BrokerMachineConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ConfigurationSlotUid | Unique identifier of the configuration slot to associate with this machine configuration. | true | true (ByPropertyName) | None |
| LeafName | Name of the new machine configuration. This must be unique amongst the machine configurations associated with the same configuration slot. | true | true (ByPropertyName) | None |
| Policy | A binary array of encoded settings (policy) data created with the SDK snap-in that matches the SettingsGroup of the configuration slot. | true | true (ByPropertyName) | None |
| Description | Description of the new machine configuration. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Machineconfiguration
New-BrokerMachineConfiguration returns the newly created configuration
## Notes
Delegated Administration can be used to restrict the configuration slots that an administrator can use and hence which components of the system that can be configured.
## Examples

### Example 1
```
New-BrokerMachineConfiguration -LeafName "Finance Department" -Description "Finance Dept. User Profile Management policy" -Policy $policy -ConfigurationSlotUid $csUid
```
#### Description
Creates a new configuration named "%SlotName%\\Finance Department" where %SlotName% is the name of the configuration slot having the Uid \$csUid. The encoded settings in the \$policy variable must match the SettingsGroup of the configuration slot having the Uid \$csUid.
