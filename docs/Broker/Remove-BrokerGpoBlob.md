
# Remove-Brokergpoblob
Remove a GPO blob.
## Syntax
```
Remove-BrokerGpoBlob [-InputObject] <GpoBlob[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Remove a GPO blob. If the blob is the default site blob, its policies are removed and the settings and filters defined for the policies are also removed. But the blob itself cannot be removed. Removing the default site blob is equivalent to erasing all the data in the site blob. If the blob is not the default site blob, the blob and the policies, settings, and filters defined for those policies are also used. The blob entry is also removed.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the GPO blob objects to remove. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Gpoblob
Remove-BrokerGpoBlob removes a GPO blob object.
## Examples

### Example 1
```
C:\PS> Remove-BrokerGpoBlob
```
#### Description
Remove all the blobs in the database.
