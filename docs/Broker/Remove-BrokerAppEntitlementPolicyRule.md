
# Remove-Brokerappentitlementpolicyrule
Deletes an application rule from the site's entitlement policy.
## Syntax
```
Remove-BrokerAppEntitlementPolicyRule [-InputObject] <AppEntitlementPolicyRule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerAppEntitlementPolicyRule [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerAppEntitlementPolicyRule cmdlet deletes an application rule from the site's entitlement policy.

An application rule in the entitlement policy defines the users who are allowed per-session access to a machine to run one or more applications published from the rule's desktop group.

Deleting a rule does not affect existing sessions launched using the rule, but users cannot reconnect to those sessions if they are subsequently disconnected.


## Related Commands

* [New-BrokerAppEntitlementPolicyRule](./New-BrokerAppEntitlementPolicyRule/)
* [Get-BrokerAppEntitlementPolicyRule](./Get-BrokerAppEntitlementPolicyRule/)
* [Set-BrokerAppEntitlementPolicyRule](./Set-BrokerAppEntitlementPolicyRule/)
* [Rename-BrokerAppEntitlementPolicyRule](./Rename-BrokerAppEntitlementPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The application rule to be deleted from the entitlement policy. | true | true (ByValue) |  |
| Name | The name of the application rule to be deleted from the entitlement policy. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Appentitlementpolicyrule
The application rule to be deleted from the entitlement policy.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerAppEntitlementPolicyRule 'Temp Workers'
```
#### Description
Deletes the application rule called Temp Workers from the entitlement policy rule. Existing application sessions launched using that rule are not affected, but users cannot reconnect to those sessions if they are subsequently disconnected.
### Example 2
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'

C:\PS> Get-BrokerAppEntitlementPolicyRule -DesktopGroupUid $dg.Uid | Remove-BrokerAppEntitlementPolicyRule
```
#### Description
Deletes the application rule from the entitlement policy rule applied to the Customer Support desktop group. This effectively removes all access to the applications published from this group. Existing application sessions are not affected, but users cannot reconnect to those sessions if they are subsequently disconnected.
