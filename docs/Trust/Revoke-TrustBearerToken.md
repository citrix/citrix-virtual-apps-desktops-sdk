
# Revoke-Trustbearertoken
Revokes the user's current bearer token.
## Syntax
```
Revoke-TrustBearerToken [-BearerToken] <String> [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Revokes the user's current bearer token.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | true | true (ByValue) |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### 

## Examples

### Example 1
```
Revoke-TrustBearerToken
```
#### Description
Revokes any bearer token issued for the current user.
