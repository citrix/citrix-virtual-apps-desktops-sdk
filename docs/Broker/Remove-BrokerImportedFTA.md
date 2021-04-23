
# Remove-Brokerimportedfta
Deletes one or more imported file type associations.
## Syntax
```
Remove-BrokerImportedFTA -DesktopGroupUids <Int32[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Deletes all of the imported file type associations belonging to one or more desktop groups. At least one desktop group must be specified.

Imported file type associations are grouped together based on the desktop group of the machine from which they were imported. All file types for a desktop group are deleted. There is no mechanism for deleting a subset imported file type associations for a specific desktop group.

Imported file type associations are different from configured file type associations. Imported file type associations are lists of known file type associations for a given desktop group. Configured file type associations are those that are actually associated with published applications for the purposes of content redirection.


## Related Commands

* [Get-BrokerImportedFTA](./Get-BrokerImportedFTA/)
* [Update-BrokerImportedFTA](./Update-BrokerImportedFTA/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DesktopGroupUids | Deletes the imported file type associations belonging to specified desktop groups. | true | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Int32\[\]
An array of Uids for the desktop groups can be supplied as input. The desktop groups must be of the Private or Shared desktop kind.
## Return Values

### None

## Notes
If an imported file type association is used to create a new configured file type association and the imported file type association is subsequently deleted, the configured file type association is not affected.
## Examples

### Example 1
```
C:\PS> $dg = Get-BrokerDesktopGroup -Name "Sales VMs"

C:\PS> Remove-BrokerImportedFTA -DesktopGroupUids $dg.Uid
```
#### Description
Deletes all imported file type associations belonging to the "Sales VMs" desktop group.
