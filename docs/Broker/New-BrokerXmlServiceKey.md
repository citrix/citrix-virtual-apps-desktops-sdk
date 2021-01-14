
# New-Brokerxmlservicekey
Generate a new 256 bit, base64 encoded, XML Service Key
## Syntax
```
New-BrokerXmlServiceKey [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
To be used with the Set-BrokerSite Cmdlet to set the two XmlServiceKey properties.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None

## Return Values

### String

## Examples

### Example 1
```
C:\PS> $xmlServiceKey1 = New-BrokerXmlServiceKey

          C:\PS> Set-BrokerSite -XmlServiceKey1 $xmlServiceKey1
```
#### Description
Sets XmlServiceKey1 in the Site settings
