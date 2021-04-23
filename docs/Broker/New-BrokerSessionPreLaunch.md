
# New-Brokersessionprelaunch
Creates a new session pre-launch setting for a desktop group.
## Syntax
```
New-BrokerSessionPreLaunch [-DesktopGroupName] <String> [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerSessionPreLaunch -DesktopGroupUid <Int32> [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerSessionPreLaunch cmdlet is used to define a session pre-launch setting for a desktop group.

Note that each desktop group can only have a single session pre-launch setting. Session pre-launch only applies to application sessions.


## Related Commands

* [Get-BrokerSessionPreLaunch](./Get-BrokerSessionPreLaunch/)
* [Set-BrokerSessionPreLaunch](./Set-BrokerSessionPreLaunch/)
* [Remove-BrokerSessionPreLaunch](./Remove-BrokerSessionPreLaunch/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DesktopGroupName | The name of the desktop group that this pre-launch setting is applied to. | true | true (ByPropertyName) |  |
| DesktopGroupUid | The Uid of the desktop group that this pre-launch setting is applied to. | true | true (ByPropertyName) |  |
| Enabled | Boolean that indicates if the new session pre-launch is enabled. | false | true (ByPropertyName) | true |
| MaxAverageLoadThreshold | Specifies the average load threshold across the desktop group. When the threshold hits, pre-launched sessions across the group be terminated to reduce load. Sessions that have been pre-launched the longest will be chosen first. | false | true (ByPropertyName) | 0 |
| MaxLoadPerMachineThreshold | Specifies the maximum load threshold per machine in the desktop group. When the threshold hits, pre-launched sessions on each loaded machine will be terminated to reduce load. Sessions that have been pre-launched the longest will be chosen first. | false | true (ByPropertyName) | 0 |
| MaxTimeBeforeDisconnect | Specifies the time by which a pre-launched session will be disconnected. The disconnect timer is optional, but when specified the terminate timer needs to be also set. The disconnect time cannot be greater than the terminate time. When the disconnect and terminate times are the same, the terminate timer takes precedence. The disconnect timer needs to be paired with a session termination condition like the terminate timer or one of load threshold settings. | false | true (ByPropertyName) | 15 minutes |
| MaxTimeBeforeTerminate | Specifies the time by which a pre-launched session will be terminated. The terminate timer is not optional when timers are configured. When the disconnect and terminate times are the same, the terminate timer takes precedence. | false | true (ByPropertyName) | 8 hours |
| UserFilterEnabled | Specifies whether the session pre-launch's user filter is enabled or disabled. Where the user filter is enabled, pre-launch is enabled only to users who appear in the filter (either explicitly or by virtue of group membership). | false | true (ByPropertyName) | false |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Depends On Parameter
Parameters can be piped by property name.
## Return Values

### Citrix.Broker.Admin.Sdk.Sessionprelaunch
New-BrokerSessionPreLaunch returns a session pre-launch object.
## Examples

### Example 1
```
C:\PS> New-BrokerSessionPreLaunch -DesktopGroupName test -Enabled $true -MaxTimeBeforeDisconnect 0:30 -MaxTimeBeforeTerminate 1:00
```
#### Description
Creates a new session pre-launch setting with a disconnect timer of 30 minutes and terminate timer of 1 hour.
