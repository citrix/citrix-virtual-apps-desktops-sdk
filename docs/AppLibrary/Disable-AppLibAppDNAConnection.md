
# Disable-Applibappdnaconnection
Disables Citrix Studio integration with AppDNA.
## Syntax
```
Disable-AppLibAppDNAConnection [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Disables Citrix Studio integration with the configured AppDNA connection.


## Related Commands

* [Enable-AppLibAppDNAConnection](./Enable-AppLibAppDNAConnection/)
* [Get-AppLibAppDNAConnection](./Get-AppLibAppDNAConnection/)
* [Set-AppLibAppDNAConnection](./Set-AppLibAppDNAConnection/)
* [Remove-AppLibAppDNAConnection](./Remove-AppLibAppDNAConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Void

## Notes
The configured connection details are not removed or modified in anyway, only disabled.
## Examples

### Example 1
```
C:\PS>Disable-AppLibAppDNAConnection
```
#### Description
Disables Citrix Studio integration with the configured AppDNA connection.
