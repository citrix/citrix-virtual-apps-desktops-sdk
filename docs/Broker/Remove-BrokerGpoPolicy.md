
# Remove-Brokergpopolicy
Remove a GPO policy.
## Syntax
```
Remove-BrokerGpoPolicy [-InputObject] <GpoPolicy[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Remove a GPO policy.


## Related Commands

* [Get-BrokerGpoPolicy](./Get-BrokerGpoPolicy/)
* [New-BrokerGpoPolicy](./New-BrokerGpoPolicy/)
* [Set-BrokerGpoPolicy](./Set-BrokerGpoPolicy/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the GPO policy object to remove. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Gpopolicy
You can pipe GPO policies to Remove-BrokerGpoPolicy.
## Return Values

### None

## Notes
Removing a policy changes the priorities of other existing policies.
## Examples

### Example 1
```
C:\PS> Remove-BrokerGpoPolicy -PolicyName 'Test'
```
#### Description
Remove the policy named 'Test'.
### Example 2
```
C:\PS> Get-BrokerGpoPolicy -Name '\*test\*' | Remove-BrokerGpoPolicy
```
#### Description
Remove all policies that have the word 'test' in their names.
