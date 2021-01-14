
# Start-Brokernaturaldesktopgrouprebootcycle
Reboots all machines from the specified desktop group when they are not in use.
## Syntax
```
Start-BrokerNaturalDesktopGroupRebootCycle [-InputObject] <DesktopGroup[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Creating a natural reboot cycle for a desktop group ensures that all machines in the group are running the most recent image for the group.

The machines are rebooted in a non-disruptive manner, allowing machines that are in use to continue working and be restarted only after they become idle.


## Related Commands

* [Start-BrokerRebootCycle](./Start-BrokerRebootCycle/)
* [Start-BrokerDesktopGroupRebootCycle](./Start-BrokerDesktopGroupRebootCycle/)
* [Start-BrokerNaturalRebootCycle](./Start-BrokerNaturalRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Reboots all machines from this input desktop group. The desktop groups can be specified using UID values, name values (including wildcards) or desktop group objects. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Desktopgroup
Desktop Groups may be specified through pipeline input. The desktop groups can be specified using UID values, name values (including wildcards) or desktop groups objects
## Return Values

### None

## Notes
Natural reboot cycles do not apply to non-power managed machines or multi-session desktop groups
## Examples

### Example 1
```
$dg = Get-BrokerDesktopGroup -Uid 1

          Start-BrokerNaturalDesktopGroupRebootCycle -InputObject $dg
```
#### Description
The above code applies a natural reboot cycle on desktop group with Id 1
