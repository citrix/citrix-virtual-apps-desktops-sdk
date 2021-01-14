
# Get-Applibappvapplication
Gets the details of an a App-V application held in the application library.
## Syntax
```
Get-AppLibAppVApplication [[-Uid] <Int32>] [-Name <String>] [-AppVPackageUid <Int32>] [-Description <String>] [-RetrieveIcon <Boolean>] [-RetrievePolicy <Boolean>] [-RetrieveUsers <Boolean>] [-RetrieveMetadata <Boolean>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The application library holds the information required to find and launch an App-V application on a client VDA.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | The AppLibrary's internal UID of the App-V application. | false | true (ByPropertyName) |  |
| Name | The name of the application in the the App-V package. | false | true (ByPropertyName) |  |
| AppVPackageUid | The AppLibrary's internal UID of the App-V package that contains the application. | false | true (ByPropertyName) |  |
| Description | A description of the application. | false | false |  |
| RetrieveIcon | A switch to indicate whether to return the application's icon data. | false | false |  |
| RetrievePolicy | A switch to indicate whether to return the application's policy blob | false | false |  |
| RetrieveUsers | A switch to indicate whether to return the application's associated users | false | false |  |
| RetrieveMetadata | A switch to indicate whether to return the application's metadata | false | false |  |
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

### Citrix.Applibrary.Sdk.Appvapplication
An object representing the details required to launch the App-V application.
## Notes
Pass in the App-V application's UID to retrieve a single application.<br>    Pass in a package UID to retrieve all of the applications in that package.<br>    Call the cmdlet without any parameters to retrieve all of the applications in the library.
## Examples

### Example 1
```
Get-AppLibAppVApplication
```
#### Description
Gets the details for all of the App-V applications in the library.
### Example 2
```
Get-AppLibAppVApplication -Name "MyApp"
```
#### Description
Gets the details of the App-V application named MyApp.
### Example 3
```
Get-AppLibAppVApplication -AppVPackageUid 15
```
#### Description
Gets the details of all of the App-V applications in the specified package.
### Example 4
```
Get-AppLibAppVApplication -RetrieveMetadata $false
```
#### Description
Gets the details of all App-V applications without the metadata
