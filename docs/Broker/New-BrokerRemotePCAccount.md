
# New-Brokerremotepcaccount
Create a new RemotePCAccount.
## Syntax
```
New-BrokerRemotePCAccount -CatalogUid <Int32> -OU <String> [-AllowSubfolderMatches <Boolean>] [-MachinesExcluded <String[]>] [-MachinesIncluded <String[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Create a new RemotePCAccount. A RemotePCAccount defines machine filters to support Remote PC automation adding unconfigured machines to catalogs.


## Related Commands

* [Get-BrokerRemotePCAccount](./Get-BrokerRemotePCAccount/)
* [Set-BrokerRemotePCAccount](./Set-BrokerRemotePCAccount/)
* [Remove-BrokerRemotePCAccount](./Remove-BrokerRemotePCAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| CatalogUid | Specifies the catalog which Remote PC automation adds an unconfigured machine to if it matches this RemotePCAccount. | true | true (ByPropertyName) |  |
| OU | Specifies the DN of an AD container, or has the special value 'any'.<br>When an AD container is specified a machine may only match with the RemotePCAccount when the AD computer object is located relative to the OU.<br>When 'any' is specified the location of the AD computer object is ignored for purposes of matching this RemotePCAccount. The machine must still meet the MachinesIncluded and MachinesExcluded filters for a match to occur.<br>In the event that a machine matches with multiple RemotePCAccounts then the RemotePCAccount OU with the longest canonical name takes precedence. The special 'any' OU is treated as lowest priority.<br>Note that the OU value of every RemotePCAccount must be unique, and this includes only one 'any' entry being permitted. | true | true (ByPropertyName) | null |
| AllowSubfolderMatches | When true a machine matches this RemotePCAccount if the AD computer object exists within the container specified by the OU property, or within a child container of the OU.<br>When false the AD computer object only matches if it exists directly in the AD container specified by the OU property.<br>This property is not meaningful when OU has the special value 'any'. | false | true (ByPropertyName) | false |
| MachinesExcluded | MachinesExcluded specifies a set of strings that can include asterisk wildcards. If a machine name matches any entries in MachinesExcluded then it cannot match with this RemotePCAccount regardless of whether there is a MachinesIncluded match.<br>Matches are performed against the domain name joined with the machine name by a backslash (DOMAIN\\MACHINE), e.g.:<br>DOMAIN1\\M\*<br>DOMAIN\*\\M\*<br>\*\\M\* | false | true (ByPropertyName) | @() |
| MachinesIncluded | MachinesIncluded specifies a set of strings that can include asterisk wildcards. A machine may only match with this RemotePCAccount if it matches a MachinesIncluded entry and does not match any MachinesExcluded entries.<br>Matches are performed against the domain name joined with the machine name by a backslash (DOMAIN\\MACHINE), e.g.:<br>DOMAIN1\\M\*<br>DOMAIN\*\\M\*<br>\*\\M\* | false | true (ByPropertyName) | @('\*') |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Remotepcaccount
The newly created RemotePCAccount.
## Examples

### Example 1
```
C:\PS> New-BrokerRemotePCAccount -OU 'ou=MyOU,dc=MyDomain,dc=com' -CatalogUid 42
```
#### Description
Create a RemotePCAccount that adds unconfigured machines with computer objects in MyOU, into catalog 42.
### Example 2
```
C:\PS> New-BrokerRemotePCAccount -OU 'any' -CatalogUid 42 -MachinesIncluded @('DOMAIN1\\*') -MachinesExcluded @('DOMAIN1\\*JOHNDOE\*')
```
#### Description
Create a RemotePCAccount matching unconfigured machines from DOMAIN1, except those with hostnames containing JOHNDOE, and add them to catalog 42.
### Example 3
```
C:\PS> New-BrokerRemotePCAccount -OU 'any' -CatalogUid 42
```
#### Description
Create a RemotePCAccount that matches any unconfigured machine, causing automation to add matching machines to catalog 42.
