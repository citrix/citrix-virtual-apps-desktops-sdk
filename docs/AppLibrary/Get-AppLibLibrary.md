
# Get-Appliblibrary
Gets the details of a library maintained by the AppLibrary service.
## Syntax
```
Get-AppLibLibrary [[-Name] <String>] [-Uid <Int32>] [-Description <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The AppLibrary service maintains information about various libraries. Network locations that are monitored for changes to the App-V packages are stored there.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | The name of the application library. | false | true (ByValue, ByPropertyName) |  |
| Uid | The AppLibrary's internal UID of the library. | false | true (ByPropertyName) |  |
| Description | A description of the application library. | false | false |  |
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

### Citrix.Applibrary.Sdk.Library
An object representing the details required to maintain a library of App-V applications.
## Notes
Pass in a library UID to retrieve only that specific library.<br>    Call the cmdlet without any parameters to retrieve all of the libraries maintained by the AppLibrary service.<br>    The 'Manual' library is not actively monitored and is designed to be managed by the user for ad-hoc storage of packages in unstructured locations.
## Examples

### Example 1
```
Get-AppLibLibrary
```
#### Description
Gets the details of all of the libraries maintained by the AppLibrary service.
### Example 2
```
Get-AppLibLibrary -Name "Manual"
```
#### Description
Gets the details of the library named Manual.
### Example 3
```
Get-AppLibLibrary -Uid 1
```
#### Description
Gets the details of the specified library.
