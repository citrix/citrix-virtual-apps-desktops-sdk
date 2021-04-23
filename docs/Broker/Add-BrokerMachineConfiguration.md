
# Add-Brokermachineconfiguration
Adds a machine configuration to a desktop group.
## Syntax
```
Add-BrokerMachineConfiguration [-InputObject] <MachineConfiguration[]> [-Application <Application>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Add-BrokerMachineConfiguration [-Name] <String> [-Application <Application>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Associates a machine configuration with a desktop group. The settings in the machine configuration are then applied to the machines in the desktop group.


## Related Commands

* [New-BrokerMachineConfiguration](./New-BrokerMachineConfiguration/)
* [Set-BrokerMachineConfiguration](./Set-BrokerMachineConfiguration/)
* [Rename-BrokerMachineConfiguration](./Rename-BrokerMachineConfiguration/)
* [Remove-BrokerMachineConfiguration](./Remove-BrokerMachineConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Machine configuration to add to the desktop group. | true | true (ByValue) |  |
| Name | Name of a machine configuration to add to the desktop group. | true | true (ByPropertyName) |  |
| Application | The application to which the machine configurations are added, specified by name, Uid, or instance. | false | true (ByValue) |  |
| DesktopGroup | The desktop group to which the machine configurations are added, specified by name, Uid, or instance. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Machineconfiguration
The machine configuration to add to the desktop group.
## Return Values

### None

## Examples

### Example 1
```
Add-BrokerMachineConfiguration -Name UPM\Conf1 -DesktopGroup 1
```
#### Description
Adds the machine configuration named UPM\\Conf1 to the desktop group with Uid 1.
### Example 2
```
$mc | Add-BrokerMachineConfiguration -DesktopGroup AdminDesktops
```
#### Description
Adds the machine configuration \$mc to the desktop group named "AdminDesktops".
