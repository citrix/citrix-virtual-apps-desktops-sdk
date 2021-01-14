
# Get-Configedgeserver
Gets Edge Servers configured for this site
## Syntax
```
Get-ConfigEdgeServer [[-Name] <String>] [-Uid <Guid>] [-Description <String>] [-MachineAddress <String>] [-Metadata <String>] [-Sid <String>] [-TenantId <Guid>] [-Uuid <Guid>] [-ZoneName <String>] [-ZoneUid <Guid>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves Edge Servers matching the specified criteria. If no parameters specified, returns all known Edge Servers


## Related Commands

* [New-ConfigEdgeServer](./New-ConfigEdgeServer/)
* [Set-ConfigEdgeServer](./Set-ConfigEdgeServer/)
* [Rename-ConfigEdgeServer](./Rename-ConfigEdgeServer/)
* [Remove-ConfigEdgeServer](./Remove-ConfigEdgeServer/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Gets the edge servers with the specified name | false | true (ByValue, ByPropertyName) |  |
| Uid | Gets the edge servers with the specified UID | false | true (ByPropertyName) |  |
| Description | Gets the edge servers with the specified description | false | false |  |
| MachineAddress | Gets the edge servers with the specified machine address | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Sid | Gets the edge servers with the specified SID value | false | false |  |
| TenantId | Gets the edge servers associated with the specified Tenant ID | false | false |  |
| Uuid | Gets the edge servers with the specified uuid | false | false |  |
| ZoneName | Gets the edge servers located in the given zone specified by zone name | false | false |  |
| ZoneUid | Gets the edge servers located in the given zone specified by zone UID | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Config\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_Config\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Configuration.Sdk.Edgeserver
Get-ConfigEdgeServer returns an object for each matching Edge Server object.
## Examples

### Example 1
```
C:\PS> Get-ConfigEdgeServer -ZoneName MyZone
```
#### Description
This command returns all edge servers in the zone named MyZone
### Example 2
```
C:\PS> Get-ConfigEdgeServer -Sid 21-3623811015-3361044348-30300820
```
#### Description
This command returns the edge server with the specified SID value
