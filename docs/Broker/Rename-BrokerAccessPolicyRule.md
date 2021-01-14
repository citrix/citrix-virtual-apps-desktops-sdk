
# Rename-Brokeraccesspolicyrule
Renames a rule in the site's access policy.
## Syntax
```
Rename-BrokerAccessPolicyRule [-InputObject] <AccessPolicyRule[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Rename-BrokerAccessPolicyRule [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Rename-BrokerAccessPolicyRule cmdlet renames a rule in the site's access policy. The Name property of the rule is changed.

An access policy rule defines a set of connection filters and access control rights relating to a desktop group. These allow fine-grained control of what access is granted to a desktop group based on details of, for example, a user's endpoint device, its address, and the user's identity.


## Related Commands

* [New-BrokerAccessPolicyRule](./New-BrokerAccessPolicyRule/)
* [Get-BrokerAccessPolicyRule](./Get-BrokerAccessPolicyRule/)
* [Set-BrokerAccessPolicyRule](./Set-BrokerAccessPolicyRule/)
* [Remove-BrokerAccessPolicyRule](./Remove-BrokerAccessPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The access policy rule to be renamed. | true | true (ByValue) |  |
| Name | The existing name of the access policy rule to be renamed. | true | true (ByPropertyName) |  |
| NewName | The new name for the access policy rule being renamed. The new name must not match that of any other existing rules in the policy. | true | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Accesspolicyrule
The access policy rule to be renamed.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Accesspolicyrule
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AccessPolicyRule object.
## Examples

### Example 1
```
C:\PS> Rename-BrokerAccessPolicyRule 'Sales' -NewName 'TeleSales'
```
#### Description
Renames the access policy rule called Sales to TeleSales. The new name of the rule must be unique in the access policy.
