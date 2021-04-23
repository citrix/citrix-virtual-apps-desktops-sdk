
# Set-Brokersessionlinger
Updates the values of one or more desktop group session linger settings.
## Syntax
```
Set-BrokerSessionLinger [-InputObject] <SessionLinger[]> [-PassThru] [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerSessionLinger [-DesktopGroupName] <String> [-PassThru] [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerSessionLinger cmdlet is used to alter the settings of an existing desktop group session linger setting.


## Related Commands

* [New-BrokerSessionLinger](./New-BrokerSessionLinger/)
* [Get-BrokerSessionLinger](./Get-BrokerSessionLinger/)
* [Remove-BrokerSessionLinger](./Remove-BrokerSessionLinger/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The session linger to be modified. | true | true (ByValue) |  |
| DesktopGroupName | The name of the desktop group whose session linger setting is to be modified. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Enabled | Boolean that indicates if the session linger setting is to be enabled or disabled. | false | false |  |
| MaxAverageLoadThreshold | Specifies the average load threshold across the desktop group. When the threshold hits, lingering sessions across the group be terminated to reduce load. Sessions that have been lingering the longest will be chosen first. | false | false |  |
| MaxLoadPerMachineThreshold | Specifies the maximum load threshold per machine in the desktop group. When the threshold hits, lingering sessions on each loaded machine will be terminated to reduce load. Sessions that have been lingering the longest will be chosen first. | false | false |  |
| MaxTimeBeforeDisconnect | Specifies the time by which a lingering session will be disconnected. The disconnect time cannot be greater than the terminate timer (if enabled). When the disconnect and terminate times are the same, the terminate time takes precedence. | false | false |  |
| MaxTimeBeforeTerminate | Specifies the time by which a lingering session will be terminated. When the disconnect and terminate times are the same, the terminate time takes precedence. | false | false |  |
| UserFilterEnabled | Specifies whether the session linger's user filter is enabled or disabled. Where the user filter is enabled, lingering is enabled only to users who appear in the filter (either explicitly or by virtue of group membership). | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Sessionlinger
Session linger settings may be specified through pipeline input.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Sessionlinger
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.SessionLinger object.
## Examples

### Example 1
```
C:\PS> Set-BrokerSessionLinger -DesktopGroupName Accounting -MaxTimeBeforeDisconnect 0:10
```
#### Description
Sets the disconnect time for the session linger setting associated with desktop group named Accounting.
