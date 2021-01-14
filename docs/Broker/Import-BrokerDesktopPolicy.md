
# Import-Brokerdesktoppolicy
Sets the site wide Citrix Group Policy settings for the site.
## Syntax
```
Import-BrokerDesktopPolicy [-Policy] <Byte[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Import-BrokerDesktopPolicy sets the site wide Citrix Group Policy settings. A successful call to this cmdlet will result in the supplied data being uploaded to every machine in the site prior to its next session launch.


## Related Commands

* [Export-BrokerDesktopPolicy](./Export-BrokerDesktopPolicy/)
* [New-BrokerConfigurationSlot](./New-BrokerConfigurationSlot/)
* [New-BrokerMachineConfiguration](./New-BrokerMachineConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Policy | The configuration data containing the Citrix Group Policy settings to apply to every machine in the site. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### System.Byte\[\]
The configuration data as an opaque binary blob.
## Return Values

### None

## Notes
Import-BrokerDesktopPolicy performs a specialized operation. Direct usage of it in scripts is discouraged, and could result in data corruption. It is recommended that this operation be performed via the Citrix Studio.
## Examples

### Example 1
```
C:\PS> Import-BrokerDesktopPolicy $policyData
```
#### Description
This command sets the Citrix Group Policy settings in the site. These policy settings are then applied to every machine prior to the next session launch.
