
# New-Brokericon
Creates a new icon.
## Syntax
```
New-BrokerIcon [-EncodedIconData] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Accepts Base64 encoded .ICO format icon data, stores it in the database and returns an Icon object containing the Uid assigned to it.

New-BrokerIcon can be used with the Get-BrokerIcon cmdlet to obtain the Base64 icon. See Examples for a demonstration.


## Related Commands

* [Get-BrokerIcon](./Get-BrokerIcon/)
* [Remove-BrokerIcon](./Remove-BrokerIcon/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| EncodedIconData | Specifies the Base64 encoded .ICO format icon data. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Icon
Returns an Icon object.
## Examples

### Example 1
```
C:\PS> $ctxIcon = Get-BrokerIcon -FileName C:\Windows\System32\notepad.exe -index 0

C:\PS> $brokerIcon = New-BrokerIcon -EncodedIconData $ctxIcon.EncodedIconData

C:\PS> $desktopGroup = Get-BrokerDesktopGroup -Name 'MyDesktopGroup'

C:\PS> Set-BrokerDesktopGroup $desktopGroup -IconUid $brokerIcon.Uid
```
#### Description
Extracts the first icon resource from notepad.exe, and sets this as the icon for a desktop group.
