
# Remove-Brokerremotepcaccount
Delete RemotePCAccounts from the system.
## Syntax
```
Remove-BrokerRemotePCAccount [-InputObject] <RemotePCAccount[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Delete RemotePCAccounts from the site.


## Related Commands

* [Get-BrokerRemotePCAccount](./Get-BrokerRemotePCAccount/)
* [New-BrokerRemotePCAccount](./New-BrokerRemotePCAccount/)
* [Set-BrokerRemotePCAccount](./Set-BrokerRemotePCAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the RemotePCAccounts to delete. | true | true (ByValue) | null |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Remotepcaccount
You can pipe the RemotePCAccounts to be deleted into this cmdlet.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerRemotePCAccount 42
```
#### Description
Delete RemotePCAccount 42.
### Example 2
```
C:\PS> Get-BrokerRemotePCAccount -OU 'any' | Remove-BrokerRemotePCAccount
```
#### Description
Delete the 'any' OU RemotePCAccount.
### Example 3
```
C:\PS> Get-BrokerRemotePCAccount | Remove-BrokerRemotePCAccount
```
#### Description
Delete all RemotePCAccounts.
