
# Set-Brokerdesktopgroupwebhook
Adjusts the settings of a webhook for a desktop group
## Syntax
```
Set-BrokerDesktopGroupWebhook [-InputObject] <DesktopGroupWebhook[]> [-PassThru] [-Address <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet is used to alter the settings of a webhook for a desktop group


## Related Commands

* [Get-BrokerDesktopGroup](./Get-BrokerDesktopGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The webhook object to alter the settings. | true | true (ByValue) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Address | Specified the new URL for the webhook. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Desktopgroupwebhook
You can pipe webhooks to this cmdlet
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Desktopgroupwebhook
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.DesktopGroupWebhook object.
## Examples

### Example 1
```
C:\PS> Get-BrokerDesktopGroupWebhook -DesktopGroupUid 1 | Set-BrokerDesktopGroupWebhook -Address "http://citrix.com/example2"
```
#### Description
Changes the URL of the webhook for the desktop group with Uid 1
