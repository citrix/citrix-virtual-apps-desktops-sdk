
# Get-Brokericon
Get stored icons.
## Syntax
```
Get-BrokerIcon -Uid <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerIcon [-Metadata <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerIcon -FileName <String> [-ServerName <String>] [-Index <Int32>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Reads a specific icon by Uid, or enumerates icons by passing no Uid.


### Brokericon Object
The BrokerIcon object represents a single instance of an icon. It contains the following properties:


  * EncodedIconData (System.String) The Base64 encoded .ICO format of the icon.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata for this command

  * Uid (System.Int32) The UID of the icon itself.


## Related Commands

* [New-BrokerIcon](./New-BrokerIcon/)
* [Remove-BrokerIcon](./Remove-BrokerIcon/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the icon specified by unique identifier. | true | false |  |
| FileName | Specifies the name of a file from which to read the icon data. If the ServerName parameter is used, the FileName must be an absolute path. | true | true (ByPropertyName) |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| ServerName | Specifies the name of the server. If the -FileName parameter refers to content or to a URL, the icon associated with the file type or URL is retrieved from the given server.  Therefore, the server specified should have a file type handler installed for the given file type.  If a local file path is specified, the server name refers to the server on which the file is located.  If a UNC path is specified, the server name is unused. | false | true (ByPropertyName) |  |
| Index | Specifies the zero-based icon resource index. For example, to select the first icon, specify an index of 0. Alternatively, to select the third icon, specify an index of 2.  If the specified index is larger than the number of icons in the source file or profiled application, an error will be returned. | false | true (ByPropertyName) |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Icon
Returns an Icon object for each enumerated icon.
### Ctxicon
Returns a list of zero or more icons, each in CtxIcon format. The CtxIcon.IconData property is the icon in standard Microsoft  ICO format.
## Examples

### Example 1
```
C:\PS> Get-BrokerIcon
```
#### Description
Enumerate all icons.
### Example 2
```
C:\PS> Get-BrokerIcon -Uid 1
```
#### Description
Get the icon with Uid 1.
### Example 3
```
C:\PS> Get-BrokerIcon -FileName icon1.dll
```
#### Description
Retrieves the icon data from a file named "icon1.dll" on this computer.  If this DLL contains multiple icons, all of them are returned in sequence.
### Example 4
```
C:\PS> Get-BrokerIcon -FileName c:\icons\icon1.dll -ServerName Server1 -Index 0
```
#### Description
Retrieves only the first icon from the "c:\\icons\\icon1.dll" file on Server1.
### Example 5
```
C:\PS> Get-BrokerIcon -FileName \\Server1\Share\app1.profile app1.exe -Index 0
```
#### Description
Retrieves the icon data for an application named "app1.exe", contained in an application profile named "app1.profile" located on a file share path "\\\\SERVER1\\Share".  Returns only the first icon associated with that profiled application.
