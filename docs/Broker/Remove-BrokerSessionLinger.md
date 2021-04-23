
# Remove-Brokersessionlinger
Removes a session linger setting.
## Syntax
```
Remove-BrokerSessionLinger [-InputObject] <SessionLinger[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerSessionLinger [-DesktopGroupName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerSessionLinger cmdlet is used to delete an existing session linger setting.


## Related Commands

* [New-BrokerSessionLinger](./New-BrokerSessionLinger/)
* [Get-BrokerSessionLinger](./Get-BrokerSessionLinger/)
* [Set-BrokerSessionLinger](./Set-BrokerSessionLinger/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The session linger setting to be deleted. | true | true (ByValue) |  |
| DesktopGroupName | The name of the desktop group whose session linger setting is to be removed. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Sessionlinger
Session linger settings may be specified through pipeline input.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Get-BrokerSessionLinger | Remove-BrokerSessionLinger
```
#### Description
Deletes every session linger setting for all desktop groups.
