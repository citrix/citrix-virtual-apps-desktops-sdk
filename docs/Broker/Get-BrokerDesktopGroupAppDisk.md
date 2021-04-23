
# Get-Brokerdesktopgroupappdisk
Gets the AppDisks that are being used by desktop group
## Syntax
```
Get-BrokerDesktopGroupAppDisk [[-DesktopGroupName] <String>] [-AppDiskUid <Guid>] [-AppDnaCompatibility <AppDnaCompatibility>] [-DesktopGroupUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerDesktopGroupAppDisk cmdlet returns all the AppDisks that are currently being used by the desktop groups and if they are compatible with their desktop group


### Brokerdesktopgroupappdisk Object
The BrokerDesktopGroupAppDisk object represents a single instance of a desktop group and AppDisk and if they are compatible


  * AppDiskUid (System.Guid) The Uid of the AppDisk

  * AppDnaCompatibility (Citrix.Broker.Admin.SDK.AppDnaCompatibility?) Specifies if the AppDisk is compatible with the desktop group

  * DesktopGroupName (System.String) The name of the desktop group

  * DesktopGroupUid (System.Int32) The Uid of the desktop group


## Related Commands

* [Get-BrokerDesktopGroup](./Get-BrokerDesktopGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DesktopGroupName | Gets only the entries that match the specified Desktop Group Name | false | false |  |
| AppDiskUid | Gets only the entries that match the specified AppDisk Uid | false | false |  |
| AppDnaCompatibility | Gets only the entries that match the specified AppDnaCompatibility | false | false |  |
| DesktopGroupUid | Gets only the entries that match the specified Desktop Group Uid | false | false |  |
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
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Desktopgroupappdisk
Returns an object for each enumerated Desktop Group and AppDisk combination.
## Examples

### Example 1
```
C:\PS> Get-BrokerDesktopGroupAppDisk -DesktopGroupName MyGroup
```
#### Description
Gets all the AppDisks that are assocated to the desktop group MyGroup
