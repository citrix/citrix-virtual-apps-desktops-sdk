
# Update-Trustbearertoken
Requests a renewed bearer token.
## Syntax
```
Update-TrustBearerToken [-BearerToken] <String> [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Requests a renewed bearer token.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | true | true (ByValue) |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### String
You can pipe the bearer token string into this command.
## Return Values

### 

## Examples

### Example 1
```
$bearerData = New-TrustBearerToken
```
#### Description
Obtains a bearer token for the current user and immediately refreshes it.
