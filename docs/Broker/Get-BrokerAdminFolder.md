
# Get-Brokeradminfolder
Get the admin folders in this site.
## Syntax
```
Get-BrokerAdminFolder [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerAdminFolder [[-Name] <String>] [-DirectChildAdminFolders <Int32>] [-DirectChildApplications <Int32>] [-FolderName <String>] [-LastChangeId <Guid>] [-Metadata <String>] [-ParentAdminFolderUid <Int32>] [-TotalChildApplications <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerAdminFolder cmdlet gets admin folders in this site.

Without parameters, Get-BrokerAdminFolder gets all the admin folders that have been created. You can also use the parameters of Get-BrokerAdminFolder to filter the results to just the folders you're interested in. You can also identify folders by their UIDs or their FolderNames.


### Brokeradminfolder Object
A folder for use in the administration console for organising other objects. E.g. BrokerApplication objects


  * DirectChildAdminFolders (System.Int32) The number of admin folders with this folder as a direct parent

  * DirectChildApplications (System.Int32) The number of applications in this admin folder (does not include any applications in child folders)

  * FolderName (System.String) The simple name of this folder within any parent folder

  * LastChangeId (System.Guid) A random GUID assigned whenever there is a change anywhere in the hierarchy of admin folders below this node; each change updates this value on the changed folder and all parents all the way up to the root folder. Note that nodes below any change do not have their LastChangeId value updated

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Holds any metadata associated with the admin folder

  * Name (System.String) The full name of the folder including the full parent hierarchy separated by back-slash characters and including a trailing back-slash

  * ParentAdminFolderUid (System.Int32) The UID of the parent admin folder; the root folder references itself (zero)

  * TotalChildApplications (System.Int32) The number of applications in this admin folder (including any applications in child folders)

  * Uid (System.Int32) The unique ID of the admin folder (the root folder has the value zero)


## Related Commands

* [New-BrokerAdminFolder](./New-BrokerAdminFolder/)
* [Remove-BrokerAdminFolder](./Remove-BrokerAdminFolder/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the admin folder with the specified unique identifier. | true | false |  |
| Name | Gets admin folders matching the specified name (if no trailing backslash is supplied, it is assumed). | false | false |  |
| DirectChildAdminFolders | Gets admin folders with the specified number of child folders. | false | false |  |
| DirectChildApplications | Gets admin folders with the specified number of applications (excluding those in sub-folders). | false | false |  |
| FolderName | Gets only the admin folders matching the specified simple folder name. | false | false |  |
| LastChangeId | Gets only the admin folders with the specified value for LastChangeId. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| ParentAdminFolderUid | Gets only admin folders with the specified parent admin folder UID value. | false | false |  |
| TotalChildApplications | Gets admin folders with the specified number of applications (including those in sub-folders). | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Adminfolder
Returns admin folders.
## Examples

### Example 1
```
C:\PS> Get-BrokerAdminFolder
```
#### Description
Return all administration folders.
### Example 2
```
C:\PS> Get-BrokerAdminFolder -Uid 1
```
#### Description
Get the administration folder with Uid 1.
