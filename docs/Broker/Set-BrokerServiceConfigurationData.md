
# Set-Brokerserviceconfigurationdata
Set the Service configuration data objects.
## Syntax
```
Set-BrokerServiceConfigurationData [-InputObject] <ServiceConfigurationData[]> [-PassThru] [-SettingValue <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
View the Service configuration data objects stored in the broker database. These objects if set correctly, if set overrride the values present in the windows registry


## Related Commands

* [Get-BrokerServiceConfigurationData](./Get-BrokerServiceConfigurationData/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The service configuration data object | true | true (ByValue) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| SettingValue | The value of the service setting that can be overridden and stored in the database. This must fall in the specified range as described in order to successfully set the service configuration object. Keeping the parameter as null will result in resetting of the key(It will be read from the windows registry in that case) | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Serviceconfigurationdata
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.ServiceConfigurationData object.
## Examples

### Example 1
```
Set-BrokerServiceConfigurationData Core.MaxHeartbeatIntervalMs  -SettingValue 360000
```
#### Description
Running this will set the MaxHeartbeatIntervalMs to 6 minutes
### Example 2
```
Set-BrokerServiceConfigurationData MaxHeartbeatIntervalMs
```
#### Description
Running this will reset the value of MaxHeartbeatIntervalMs and it will be read from the windows registry instead of the Broker Database
