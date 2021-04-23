
# Get-Applibisolationgrouppackage
Gets the details of an App-V package of an Isolation Group.
## Syntax
```
Get-AppLibIsolationGroupPackage [[-IsolationGroupUid] <Int32>] [-AppVPackageUid <Int32>] [-ExplicitInclusion <Boolean>] [-OrderNumber <Int32>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves the App-V package of the specified Isolation Group.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IsolationGroupUid | The AppLibrary's internal unique identifier of the Isolation Group which contains the package. | false | true (ByValue, ByPropertyName) |  |
| AppVPackageUid | The AppLibrary's internal unique identifier of the App-V package. | false | true (ByPropertyName) |  |
| ExplicitInclusion | Indicates whether the package is explicitly included in the delivery group. | false | false |  |
| OrderNumber | The order number within the Isolation Group (if the package belongs to an Isolation Group). | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_AppLib\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_AppLib\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Isolationgrouppackage
An object representing the details of an App-V package in an Isolation Group.
## Examples

### Example 1
```
Get-AppLibIsolationGroupPackage -AppVPackageUid 4 -IsolationGroupUid 15
```
#### Description
Gets the details of the App-V package with the unique identifier in the specified isolation group.
### Example 2
```
Get-AppLibIsolationGroupPackage -IsolationGroupUid 15
```
#### Description
Gets the details for all of the App-V packages in the specified isolation group.
