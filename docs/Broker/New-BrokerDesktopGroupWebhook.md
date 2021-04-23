
# New-Brokerdesktopgroupwebhook
Create a webhook for the sepcified desktop group
## Syntax
```
New-BrokerDesktopGroupWebhook -Address <String> -DesktopGroupUid <Int32> -OnEvent <WebhookTrigger> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet is used to create a webhook for the sepcified desktop group, that is invoked upon the specified event of the desktop group.


## Related Commands

* [Get-BrokerDesktopGroup](./Get-BrokerDesktopGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Address | The URL of the webhook | true | true (ByPropertyName) |  |
| DesktopGroupUid | The Uid of the desktop group to configure a webhook | true | true (ByPropertyName) |  |
| OnEvent | The event upon that the webhook is invoked, currently the only supported event is MachineRegistration.<br>For MachineRegistration, when the webhook is invoked it is HTTP POST with a JSON payload of the format: {"SamName": "value"} where the "value" is the SamName of the machine that is registering to the broker. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Desktopgroupwebhook
The set of webhooks to be added to the desktop group can be piped into this cmdlet
## Return Values

### None

## Examples

### Example 1
```
C:\PS> New-BrokerDesktopGroupWebhook –DesktopGroupUid 1 –OnEvent MachineRegistration –Address 'http://citrix.com/example'
```
#### Description
Creates a new webhook for the desktop group with Uid 1, that is to be invoked when a machine registers to the broker.&lt;br&gt;When it is invoked, a HTTP POST request is sent out to the address above with a JSON payload {"SamName": "value"} where "value" is the SAM name of registering machine.
