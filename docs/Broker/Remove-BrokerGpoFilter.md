
# Remove-Brokergpofilter
Removes a GPO filter.
## Syntax
```
Remove-BrokerGpoFilter [-InputObject] <GpoFilter[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Remove a GPO filter.


## Related Commands

* [Get-BrokerGpoFilter](./Get-BrokerGpoFilter/)
* [New-BrokerGpoFilter](./New-BrokerGpoFilter/)
* [Set-BrokerGpoFilter](./Set-BrokerGpoFilter/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the GPO filter object to remove. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Gpofilter
GPO filters may be specified through pipeline input.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerGpoFilter -FilterGuid '1234...'
```
#### Description
Remove the filter with the specified ID.
