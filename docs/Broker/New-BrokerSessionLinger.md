
# New-Brokersessionlinger
Creates a new session linger setting for a desktop group.
## Syntax
```
New-BrokerSessionLinger [-DesktopGroupName] <String> [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerSessionLinger -DesktopGroupUid <Int32> [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerSessionLinger cmdlet is used to define a session linger setting for a desktop group.

Note that each desktop group can only have a single session linger setting. Session lingering only applies to application sessions.


## Related Commands

* [Get-BrokerSessionLinger](./Get-BrokerSessionLinger/)
* [Set-BrokerSessionLinger](./Set-BrokerSessionLinger/)
* [Remove-BrokerSessionLinger](./Remove-BrokerSessionLinger/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DesktopGroupName | The name of the desktop group that this linger setting is applied to. | true | true (ByPropertyName) |  |
| DesktopGroupUid | The Uid of the desktop group that this linger setting is applied to. | true | true (ByPropertyName) |  |
| Enabled | Boolean that indicates if the new session linger is enabled. | false | true (ByPropertyName) | true |
| MaxAverageLoadThreshold | Specifies the average load threshold across the desktop group. When the threshold hits, lingering sessions across the group be terminated to reduce load. Sessions that have been lingering the longest will be chosen first. | false | true (ByPropertyName) | 0 |
| MaxLoadPerMachineThreshold | Specifies the maximum load threshold per machine in the desktop group. When the threshold hits, lingering sessions on each loaded machine will be terminated to reduce load. Sessions that have been lingering the longest will be chosen first. | false | true (ByPropertyName) | 0 |
| MaxTimeBeforeDisconnect | Specifies the time by which a lingering session will be disconnected. The disconnect timer is optional, but when specified the terminate timer needs to be also set. The disconnect time cannot be greater than the terminate time. When the disconnect and terminate times are the same, the terminate timer takes precedence. The disconnect timer needs to be paired with a session termination condition like the terminate timer or one of load threshold settings. | false | true (ByPropertyName) | 15 minutes |
| MaxTimeBeforeTerminate | Specifies the time by which a lingering session will be terminated. The terminate timer is not optional when timers are configured. When the disconnect and terminate times are the same, the terminate timer takes precedence. | false | true (ByPropertyName) | 8 hours |
| UserFilterEnabled | Specifies whether the session linger's user filter is enabled or disabled. Where the user filter is enabled, lingering is enabled only to users who appear in the filter (either explicitly or by virtue of group membership). | false | true (ByPropertyName) | false |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Depends On Parameter
Parameters can be piped by property name.
## Return Values

### Citrix.Broker.Admin.Sdk.Sessionlinger
New-BrokerSessionLinger returns a session linger object.
## Examples

### Example 1
```
C:\PS> New-BrokerSessionLinger -DesktopGroupName test -Enabled $true -MaxTimeBeforeDisconnect 0:30 -MaxTimeBeforeTerminate 1:00
```
#### Description
Creates a new session linger setting with a disconnect timer of 30 minutes and terminate timer of 1 hour.
