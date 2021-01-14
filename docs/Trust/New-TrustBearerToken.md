
# New-Trustbearertoken
Creates a new bearer token for the current user.
## Syntax
```
New-TrustBearerToken [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Creates a new bearer token for the current user. This uses the current Windows identity.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Trust.Sdk.Bearertokendata
The bearer token.
## Examples

### Example 1
```
$bearerData = New-TrustBearerToken
```
#### Description
Obtains the bearer token and stores it in the \$bearerData variable and uses it to authenticate with the Broker.
