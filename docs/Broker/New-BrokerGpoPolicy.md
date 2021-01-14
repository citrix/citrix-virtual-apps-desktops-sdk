
# New-Brokergpopolicy
Create a new GPO policy.
## Syntax
```
New-BrokerGpoPolicy -PolicyName <String> [-BlobGuid <Guid>] [-Description <String>] [-IsEnabled <Boolean>] [-IsReadOnly <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerGpoPolicy cmdlet creates a new GPO policy.


## Related Commands

* [Get-BrokerGpoPolicy](./Get-BrokerGpoPolicy/)
* [Set-BrokerGpoPolicy](./Set-BrokerGpoPolicy/)
* [Remove-BrokerGpoPolicy](./Remove-BrokerGpoPolicy/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| PolicyName | Specifies the new policy name. The name must not exist in the specified blob. | true | true (ByPropertyName) |  |
| BlobGuid | Specifies the blob the new policy will be in. If the ID is not specified, the new policy is created in the default site blob. | false | true (ByPropertyName) | None |
| Description | Specifies the description of the policy. | false | true (ByPropertyName) |  |
| IsEnabled | Specifies whether policy is enabled. | false | true (ByPropertyName) | true |
| IsReadOnly | Specifies whether the new policy is readonly. | false | true (ByPropertyName) | false |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Gpopolicy
The newly created GPO policy.
## Notes
The priority of the new policy is assigned with the lowest priority.
## Examples

### Example 1
```
C:\PS> New-BrokerGpoPolicy -PolicyName "Policy0"
```
#### Description
Create a policy named Policy0 in the default site blob.
