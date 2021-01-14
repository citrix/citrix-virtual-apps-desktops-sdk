
# Export-Brokerconfiguration
Obtains an XML document containing the configuration of the broker and optionally a script to import it into another broker
## Syntax
```
Export-BrokerConfiguration [-TargetBrokerVersion <Version>] [-ExistingImportScriptId <String>] [-ExistingConfigLastChangeTime <String>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description



## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TargetBrokerVersion | The version of the broker receiving the configuration | false | false | \$null |
| ExistingImportScriptId | The Id of the script the caller already has; a new script will be returned in the XML document if different. | false | false | \$null |
| ExistingConfigLastChangeTime | The value of ConfigLastChangeTime in the site object of any configuration already held by the caller. If nothing has changed, an empty configuration will be returned with the "Updated" attribute set to false. | false | false | \$null |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### This Cmdlet Does Not Accept Input

## Return Values

### String
The XML document
