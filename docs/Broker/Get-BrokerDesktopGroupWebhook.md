
# Get-Brokerdesktopgroupwebhook
Gets the webhook configured for desktop group
## Syntax
```
Get-BrokerDesktopGroupWebhook -Uid <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerDesktopGroupWebhook [-Address <String>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-OnEvent <WebhookTrigger>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The cmdlet returns the webhook that are currently being configured for desktop groups. Each desktop group can have up to one webhook.


### Brokerdesktopgroupwebhook Object
The BrokerDesktopGroupWebhook object represents a webhook of a desktop group that is invoked upon certain events, currently the only supported event is MachineRegistration.


  * Address (System.String) URL of the webhook

  * DesktopGroupName (System.String) The name of the desktop group

  * DesktopGroupUid (System.Int32) The Uid of the desktop group

  * OnEvent (Citrix.Broker.Admin.SDK.WebhookTrigger) The event upon that the webhook is triggered

  * Uid (System.Int32) The Uid of the webhook


## Related Commands

* [Get-BrokerDesktopGroup](./Get-BrokerDesktopGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Get only webhooks that match the specified Webhook Uid | true | false |  |
| Address | Gets only webhooks whose URL matches that specified. | false | false |  |
| DesktopGroupName | Gets only webhooks associated with desktop groups whose names match that specified. | false | false |  |
| DesktopGroupUid | Gets only webhooks associated with the specified desktop group. | false | false |  |
| OnEvent | Gets only webhooks that match the specified OnEvent. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet
## Return Values

### Citrix.Broker.Admin.Sdk.Desktopgroupwebhook
Returns an object for each enumerated Desktop Group and an Webhook combination
## Examples

### Example 1
```
C:\PS> Get-BrokerDesktopGroupWebhook -DesktopGroupUid 1
```
#### Description
Gets the webhook that is associated to the desktop group 1
