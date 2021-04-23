
# Export-Brokerdesktoppolicy
Gets the site wide Citrix Group Policy settings.
## Syntax
```
Export-BrokerDesktopPolicy [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Export-BrokerDesktopPolicy returns an array of bytes containing the site-wide Citrix Group Policy settings. These policy settings are applied to every machine in the site.


## Related Commands

* [Import-BrokerDesktopPolicy](./Import-BrokerDesktopPolicy/)
* [New-BrokerConfigurationSlot](./New-BrokerConfigurationSlot/)
* [New-BrokerMachineConfiguration](./New-BrokerMachineConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None

## Return Values

### System.Byte\[\]
The configuration data as an opaque binary blob. This will be null if no site wide Citrix Group Policy settings are in place.
## Notes
Export-BrokerDesktopPolicy performs a specialized operation. Direct usage of it in scripts is discouraged, and could result in data corruption. It is recommended that this operation only be performed via the Citrix Studio.
## Examples

### Example 1
```
C:\PS> $policy = Export-BrokerDesktopPolicy
```
#### Description
This command exports the site wide Citrix Group Policy settings.
