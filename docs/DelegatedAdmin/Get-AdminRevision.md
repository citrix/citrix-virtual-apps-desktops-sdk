
# Get-Adminrevision
Gets the current revision of the delegated administration configuration data.
## Syntax
```
Get-AdminRevision [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Delegated Administration Service maintains a revision number that is incremented whenever its configuration is changed. This command retrieves the current revision number.


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

### System.Int32
The configuration revision number
## Notes
If Int32.MaxValue is reached the value of the revision number will wrap around to Int32.MinValue.<br>    In some cases the value may be incremented by more than one.
## Examples

### Example 1
```
C:\PS> Get-AdminRevision
```
#### Description
Retrieve the current revision number.
