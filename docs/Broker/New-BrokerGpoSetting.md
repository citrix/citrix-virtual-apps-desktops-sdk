
# New-Brokergposetting
Creates a new GPO setting.
## Syntax
```
New-BrokerGpoSetting -PolicyGuid <Guid> -RegistryPath <String> -SettingName <String> -SettingState <GpoSettingState> [-SettingValue <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Creates a GPO setting for a policy.


## Related Commands

* [Get-BrokerGpoSetting](./Get-BrokerGpoSetting/)
* [Set-BrokerGpoSetting](./Set-BrokerGpoSetting/)
* [Remove-BrokerGpoSetting](./Remove-BrokerGpoSetting/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| PolicyGuid | The ID of the policy for which the filter is created. | true | true (ByPropertyName) |  |
| RegistryPath | The registry path of the setting. | true | true (ByPropertyName) |  |
| SettingName | The setting name. | true | true (ByPropertyName) |  |
| SettingState | The setting state. | true | true (ByPropertyName) |  |
| SettingValue | The setting value. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Gposetting
Outputs the GPO setting object.
## Examples

### Example 1
```
C:\PS> New-BrokerGpoSetting -PolicyGuid {123...} -SettingName SoundQuality -RegistryPath 'MultimediaPolicies\SoundQuality' -SettingState 1
```
#### Description
Creates a new 'Audio quality' setting.
