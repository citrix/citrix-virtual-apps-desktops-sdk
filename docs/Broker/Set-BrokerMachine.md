
# Set-Brokermachine
Sets properties on a machine.
## Syntax
```
Set-BrokerMachine [-InputObject] <Machine[]> [-PassThru] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-HostedMachineId <String>] [-HypervisorConnectionUid <Int32>] [-InMaintenanceMode <Boolean>] [-IsReserved <Boolean>] [-PublishedName <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerMachine [-MachineName] <String> [-PassThru] [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-HostedMachineId <String>] [-HypervisorConnectionUid <Int32>] [-InMaintenanceMode <Boolean>] [-IsReserved <Boolean>] [-PublishedName <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerMachine cmdlet sets properties on a machine or set of machines. You can specify a single machine by name or multiple machine instances can be passed to the command by piping or using the -InputObject parameter.


## Related Commands

* [Get-BrokerMachine](./Get-BrokerMachine/)
* [New-BrokerMachine](./New-BrokerMachine/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The machine instances whose properties you want to set. | true | true (ByValue) |  |
| MachineName | The machine whose properties you want to set. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| AssignedClientName | Changes the client name assignment of the machine. Set this to \$null to remove the assignment. You can assign machines to multiple users, a single client IP address, or a single client name, but only to one of these categories at a time. | false | false |  |
| AssignedIPAddress | Changes the client IP address assignment of the machine. Set this to \$null to remove the assignment. You can assign machines to multiple users, a single client IP address, or a single client name, but only to one of these categories at a time. | false | false |  |
| HostedMachineId | The unique ID by which the hypervisor recognizes the machine. This may only be set for VMs which are not provisioned by MCS. | false | false |  |
| HypervisorConnectionUid | The hypervisor connection that runs the machine. This may only be set for VMs which are not provisioned by MCS. | false | false |  |
| InMaintenanceMode | Sets whether the machine is in maintenance mode or not. A machine in maintenance mode is not available for new sessions, and for managed machines all automatic power management is disabled. | false | false |  |
| IsReserved | Specifies whether the machine should be reserved for special use, for example, for AppDisk preparation. A machine cannot be reserved if it is already a member of a desktop group. | false | false |  |
| PublishedName | The name of the machine that is displayed in StoreFront, if the machine has been published. It can be set only for private desktops. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Machine
You can pipe in the machines whose properties you want to set.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Machine
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Machine object.
## Examples

### Example 1
```
C:\PS> Set-BrokerMachine -MachineName 'MyDomain\MyMachine' -HypervisorConnectionUid 3
```
#### Description
This example specifies a machine by name and sets its hypervisor connection.
### Example 2
```
C:\PS> $machines = Get-BrokerMachine -MachineName 'MyDomain\\*'

C:\PS> Set-BrokerMachine -InputObject $machines -HypervisorConnectionUid 3
```
#### Description
This example finds all machines in domain MyDomain and sets their hypervisor connections.
### Example 3
```
C:\PS> Get-BrokerMachine -MachineName 'MyDomain\\*' | Set-BrokerMachine -HypervisorConnectionUid 3
```
#### Description
This example also finds all machines in domain MyDomain and sets their hypervisor connections.
