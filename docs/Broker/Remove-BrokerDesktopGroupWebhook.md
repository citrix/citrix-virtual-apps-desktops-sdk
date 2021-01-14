
# Remove-Brokerdesktopgroupwebhook
Remove the webhook from a desktop group
## Syntax
```
Remove-BrokerDesktopGroupWebhook [-InputObject] <DesktopGroupWebhook[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet is used to remove the configured webhook from a desktop group


## Related Commands

* [Get-BrokerDesktopGroup](./Get-BrokerDesktopGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Sepcified the webhook to remove | true | true (ByValue) | null |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Desktopgroupwebhook
You can pipe webhooks to this cmdlet.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Get-BrokerDesktopGroupWebhook -DesktopGroupUid 1 | Remove-BrokerDesktopGroupWebhook
```
#### Description
Removes the webhook configured for the desktop group with Uid 1
