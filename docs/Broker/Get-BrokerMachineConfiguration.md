
# Get-Brokermachineconfiguration
Gets machine configurations defined for this site.
## Syntax
```
Get-BrokerMachineConfiguration [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerMachineConfiguration [[-Name] <String>] [-ConfigurationSlotUid <Int32>] [-LeafName <String>] [-Metadata <String>] [-ApplicationUid <Int32>] [-DesktopGroupUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves machine configurations matching the specified criteria. If no parameters are specified this cmdlet enumerates all machine configurations.

Machine configurations contain binary arrays of settings data that are managed using SDK snap-ins. Each machine configuration is associated with a configuration slot and referenced by Name. The configuration slot restricts the settings that can be held by the machine configuration. For example, only configurations for Citrix User Profile Manager can be associated with the "User Profile Manager" slot.

See about\_Broker\_Filtering for information about advanced filtering options.


### Brokermachineconfiguration Object
The machine configuration object returned represents a named collection of related settings values that are applied to a desktop group.


  * ApplicationUids (System.Int32\[\]) List of application Uids that this machine configuration has been added to.

  * ConfigurationSlotUid (System.Int32) Uid of the associated configuration slot.

  * Description (System.String) Optional description of the machine configuration.

  * DesktopGroupUids (System.Int32\[\]) List of desktop group Uids that this machine configuration has been added to.

  * LeafName (System.String) Name of this machine configuration.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Map of metadata associated with this machine configuration.

  * Name (System.String) Unique "SlotName\\MachineConfigurationName" for this machine configuration.

  * Policy (System.Byte\[\]) A binary array of encoded settings.

  * Uid (System.Int32) Uid of this machine configuration.


## Related Commands

* [New-BrokerMachineConfiguration](./New-BrokerMachineConfiguration/)
* [Set-BrokerMachineConfiguration](./Set-BrokerMachineConfiguration/)
* [Rename-BrokerMachineConfiguration](./Rename-BrokerMachineConfiguration/)
* [Remove-BrokerMachineConfiguration](./Remove-BrokerMachineConfiguration/)
* [Add-BrokerMachineConfiguration](./Add-BrokerMachineConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Get only the machine configuration with the specified unique identifier. | true | false |  |
| Name | Get only the machine configuration with the specified name. | false | false |  |
| ConfigurationSlotUid | Get only the machine configurations associated with the specified configuration slot. | false | false |  |
| LeafName | Get only the machine configurations that have the specified leaf name. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| ApplicationUid | Get only the machine configurations that have been assigned to the specified application. | false | false |  |
| DesktopGroupUid | Get only the machine configurations that have been assigned to the specified desktop group. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Machineconfiguration
Get-BrokerMachineConfiguration returns an object for each matching machine configuration.
## Examples

### Example 1
```
Get-BrokerMachineConfiguration
```
#### Description
Retrieves a list of every defined machine configuration.
### Example 2
```
Get-BrokerMachineConfiguration -Name Receiver\Engineering
```
#### Description
Retrieves the machine configuration named "Receiver\\Engineering".
### Example 3
```
Get-BrokerMachineConfiguration -Name UPM\\*
```
#### Description
Retrieves a list of every machine configuration associated with the configuration slot named "UPM".
### Example 4
```
Get-BrokerMachineConfiguration -LeafName "Dept\*"
```
#### Description
Retrieves a list of every machine configuration with a LeafName that starts with "Dept", regardless of the associated configuration slot.
