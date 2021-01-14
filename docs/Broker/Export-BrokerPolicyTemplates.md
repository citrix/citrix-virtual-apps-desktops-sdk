
# Export-Brokerpolicytemplates
Gets the site wide Citrix Group Policy templates.
## Syntax
```
Export-BrokerPolicyTemplates [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Export-BrokerPolicyTemplates returns an array of bytes containing the site-wide Citrix Group Policy templates. These templates can be used to create new policies.


## Related Commands

* [Import-BrokerPolicyTemplates](./Import-BrokerPolicyTemplates/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None

## Return Values

### System.Management.Automation.Psobject
The policy templates data as an opaque binary blob. This will be null if no site wide Citrix Group Policy templates have been created.
## Notes
Export-BrokerPolicyTemplates performs a specialized operation. Direct usage of it in scripts is discouraged, and could result in data corruption. It is recommended that this operation only be performed via the Citrix Studio.
## Examples

### Example 1
```
C:\PS> $policy = Export-BrokerPolicyTemplates
```
#### Description
This command exports the site wide Citrix Group Policy templates.
