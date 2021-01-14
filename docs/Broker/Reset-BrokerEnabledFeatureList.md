
# Reset-Brokerenabledfeaturelist
Resets the broker's list of enabled features.
## Syntax
```
Reset-BrokerEnabledFeatureList [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Reset-BrokerLicensingConnection cmdlet resets the broker's list of enabled features.

Toggling site features on or off doesn't become effective immediately. There will typically be a delay as the changes are propagated across the site based on the scheduling of refresh logic built into the controllers.

After toggling features on or off you can run Reset-BrokerEnabledFeatureList to ensure that the broker can access the new list of enabled features immediately.

Each broker service instance holds its list of enabled features. In order for the feature list changes to be applied immediately throughout the XenDesktop site this command needs to be run on every controller in the site.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Reset-BrokerEnabledFeatureList
```
#### Description
Reset the broker's list of enabled features.
