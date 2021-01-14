
# Get-Brokerremotepcaccount
Get RemotePCAccount entries configured for this site.
## Syntax
```
Get-BrokerRemotePCAccount -Uid <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerRemotePCAccount [-AllowSubfolderMatches <Boolean>] [-CatalogUid <Int32>] [-OU <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves RemotePCAccounts matching the specified criteria. If no parameters are specified this cmdlet enumerates all RemotePCAccounts. Each RemotePCAccount object defines a set of machines either by machine name patterns or by where the machines are placed in Active Directory, and which RemotePC catalog the machines are to be associated with when they are discovered.


### Brokerremotepcaccount Object
RemotePCAccounts define a set of machines either by machine name patterns or by where the machines are placed in Active Directory, and which RemotePC catalog the machines are to be associated with when they are discovered.


  * AllowSubfolderMatches (System.Boolean) Specifies whether machines subfolders of specified AD OUs are to be considered part of the RemotePCAccount.

  * CatalogUid (System.Int32) The Uid of the RemotePC catalog to which machines in the RemotePCAccount automatically join during registration.

  * MachinesExcluded (System.String\[\]) A list of machines which are to be excluded from the RemotePCAccount. Wildcard matching is supported.

  * MachinesIncluded (System.String\[\]) A list of machines which are to be included in the RemotePCAccount. Wildcard matching is supported.

  * OU (System.String) Machines within this specified AD OU are considered part of the RemotePCAccount, unless they are in they match the MachinesExcluded

  * Uid (System.Int32) The Uid of the RemotePCAccount object.


## Related Commands

* [New-BrokerRemotePCAccount](./New-BrokerRemotePCAccount/)
* [Set-BrokerRemotePCAccount](./Set-BrokerRemotePCAccount/)
* [Remove-BrokerRemotePCAccount](./Remove-BrokerRemotePCAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the RemotePCAccount with the specified unique ID. | true | false |  |
| AllowSubfolderMatches | Gets RemotePCAccounts with the specified value of AllowSubfolderMatches. | false | false |  |
| CatalogUid | Gets RemotePCAccounts belonging to the specified Remote PC catalog. | false | false |  |
| OU | Gets the RemotePCAccount with the specified OU. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Remotepcaccount
Get-BrokerRemotePCAccount returns an object for each matching RemotePCAccount.
## Examples

### Example 1
```
C:\PS> Get-BrokerRemotePCAccount
```
#### Description
Find all RemotePCAccounts.
### Example 2
```
C:\PS> Get-BrokerRemotePCAccount -CatalogUid 42
```
#### Description
Find RemotePCAccounts belonging to Remote PC catalog 42.
