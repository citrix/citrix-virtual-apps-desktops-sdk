
# Test-Brokerentitlementpolicyrulenameavailable
Determine whether the proposed EntitlementPolicyRule Name is available for use.
## Syntax
```
Test-BrokerEntitlementPolicyRuleNameAvailable [-Name] <String[]> [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet checks whether proposed EntitlementPolicyRule Name is available for use. It returns a record for each Name indicating the availability of that Name, with \$true indicating that the Name is unused and available for use, or \$false if it is not available.


## Related Commands

* [Get-BrokerEntitlementPolicyRule](./Get-BrokerEntitlementPolicyRule/)
* [New-BrokerEntitlementPolicyRule](./New-BrokerEntitlementPolicyRule/)
* [Rename-BrokerEntitlementPolicyRule](./Rename-BrokerEntitlementPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | The EntitlementPolicyRule Name to be tested. | true | true (ByValue, ByPropertyName) |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### System.String
You can pipe a string that contains the Name to test.
## Return Values

### Citrix.Broker.Admin.Sdk.Nameavailability
The cmdlet returns a result for each Name specified. An availability of "True" indicates the Name is available for use, and "False" if it is not available.
## Examples

### Example 1
```
C:\PS> Test-BrokerEntitlementPolicyRuleNameAvailable -Name Test1
```
#### Description
Checks whether the Name "Test1" is available.
### Example 2
```
C:\PS> Test-BrokerEntitlementPolicyRuleNameAvailable @("Test1","Test2","Test3")
```
#### Description
Checks whether each of the specified names is available.
