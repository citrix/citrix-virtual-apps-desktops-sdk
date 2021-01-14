
# Set-Brokergpopolicy
Changes the properties of a GPO policy.
## Syntax
```
Set-BrokerGpoPolicy [-InputObject] <GpoPolicy[]> [-PassThru] [-Description <String>] [-IsEnabled <Boolean>] [-PolicyName <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerGpoPolicy cmdlet is used to disable or enable an existing GPO policy or to alter its properties.


## Related Commands

* [Get-BrokerGpoPolicy](./Get-BrokerGpoPolicy/)
* [New-BrokerGpoPolicy](./New-BrokerGpoPolicy/)
* [Remove-BrokerGpoPolicy](./Remove-BrokerGpoPolicy/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the GPO policy object to set. | true | true (ByValue) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Description | Specifies a new description for the policy. | false | false |  |
| IsEnabled | Enable or disable the policy. | false | false |  |
| PolicyName | Specifies a new name for the policy. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Gpopolicy
You can pipe GPO policies to be adjusted to Set-BrokerGpoPolicy.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Gpopolicy
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.GpoPolicy object.
## Examples

### Example 1
```
C:\PS> Set-BrokerGpoPolicy -PolicyName '\*test\*' -IsEnabled $true
```
#### Description
Enable all policies with names containing the word 'test'.
