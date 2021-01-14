
# Get-Brokergposetting
Gets GPO settings for a policy.
## Syntax
```
Get-BrokerGpoSetting -SettingGuid <Guid> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerGpoSetting [-PolicyGuid <Guid>] [-SettingName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieve GPO settings that meet certain criteria.


### Brokergposetting Object
A GPO setting specifies a configuration setting that controls how a VDA behaves.


  * PolicyGuid (System.Guid) The ID of the policy that owns the setting. If this ID is not specified, the setting GUID must be specified.

  * RegistryPath (System.String) The registry path on a VDA under HKLM\\Software\\Policies\\Citrix to store the value of the setting after the setting is applied.

  * SettingGuid (System.Guid) The ID of the setting. If this ID is not specified, all the settings of a policy are returned.

  * SettingName (System.String) The name of the setting. If this is specified, the setting of the specified name is returned.

  * SettingState (Citrix.Broker.Admin.SDK.GpoSettingState) Indicate the state of the setting.

  * SettingValue (System.String) The setting value.


## Related Commands

* [New-BrokerGpoSetting](./New-BrokerGpoSetting/)
* [Set-BrokerGpoSetting](./Set-BrokerGpoSetting/)
* [Remove-BrokerGpoSetting](./Remove-BrokerGpoSetting/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SettingGuid | Gets specified setting. If this parameter is not specified, all settings that belong to the policy are returned. | true | false |  |
| PolicyGuid | Specifies the policy for which the settings are retrieved. | false | false |  |
| SettingName | Gets specified setting if this parameter is specified. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Gposetting
Get-BrokerGpoSetting returns an object for each matching GPO setting object.
## Examples

### Example 1
```
C:\PS> Get-BrokerGpoSetting -SettingGuid {12345678-...}
```
#### Description
Gets the specified setting.
