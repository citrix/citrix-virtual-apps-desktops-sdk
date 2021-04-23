
# Get-Brokerimportedfta
Gets the imported file type associations.
## Syntax
```
Get-BrokerImportedFTA [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerImportedFTA [[-ExtensionName] <String>] [-ContentType <String>] [-Description <String>] [-DesktopGroupUid <Int32>] [-Edit <String>] [-EditArguments <String>] [-EditExecutableName <String>] [-HandlerName <String>] [-Open <String>] [-OpenArguments <String>] [-OpenExecutableName <String>] [-PerceivedType <String>] [-Print <String>] [-PrintTo <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns the file type associations the system imports from worker machines.

File type association associates a file extension (such as ".txt") with an application (such as Notepad). In a Citrix environment file type associations on a user device can be configured so that when an user clicks on a document it launches the appropriate published application. This is known as "content redirection".

Imported file type associations are different from configured file type associations. Imported file type associations are lists of known file type associations for a given desktop group. Configured file type associations are those that are actually associated with published applications for the purposes of content redirection.

Initially the system is not aware of any extensions, and they must be imported by the Citrix administrator. See the Update-BrokerImportedFTA cmdlet for more information.

After file type extensions are imported, this cmdlet lets the administrator review which file type associations the system is aware of. ImportedFTA objects are also used when configuring content redirection. See the New-BrokerConfiguredFTA cmdlet for more information.

The imported file type associations are grouped according to the desktop group to which they belong, because the system expects all machines in the same desktop group to have the same file type associations. That may not be true, however, across desktop groups.

Note that the ImportedFTA object has several fields that are not currently used. Only those fields that are shared with the ConfiguredFTA object are actually used in some capacity.


### Brokerimportedfta Object
The BrokerImportedFTA object represents a file type association imported from worker machines. It contains the following properties:


  * ContentType (System.String) Content type of the file, such as "text/plain" or "application/vnd.ms-excel".

  * Description (System.String) File type description, such as "Test Document", "Microsoft Word Text Document", etc.

  * DesktopGroupUid (System.Int32) The desktop group this file type belongs to.

  * Edit (System.String) Edit command with full path to executable: "C:\\Program Files (x86)\\Microsoft Office\\Office12\\WINWORD.EXE" /n /dde

  * EditArguments (System.String) The arguments used for the ‘edit’ action on files of this type. These are extracted from the full edit command, and may be empty.

  * EditExecutableName (System.String) The executable name extracted from the Edit property, no path included. This is used for matching with published apps' executable when searching for the list of extensions an application is capable of handling.

  * ExtensionName (System.String) A single file extension, such as .txt. Unique within the scope of a desktop group.

  * HandlerName (System.String) File type handler name, e.g. "Word.Document.8" or TXTFILE.

  * Open (System.String) Open command with full path to executable: "C:\\Program Files (x86)\\Microsoft Office\\Office12\\WINWORD.EXE" /n /dde

  * OpenArguments (System.String) The arguments used for the ‘open’ action on files of this type. These are extracted from the full open command, and may be empty.

  * OpenExecutableName (System.String) The executable name extracted from the Open property, no path included. This is used for matching with published apps' executable when searching for the list of extensions an application is capable of handling.

  * PerceivedType (System.String) Perceived type, such as "text".

  * Print (System.String) Print command: "C:\\Program Files (x86)\\Microsoft Office\\Office12\\WINWORD.EXE" /x /n /dde

  * PrintTo (System.String) PrintTo command: "C:\\Program Files (x86)\\Microsoft Office\\Office12\\WINWORD.EXE" /n /dde

  * Uid (System.Int32) Unique internal identifier of imported file type association.


## Related Commands

* [New-BrokerConfiguredFTA](./New-BrokerConfiguredFTA/)
* [Remove-BrokerImportedFTA](./Remove-BrokerImportedFTA/)
* [Update-BrokerImportedFTA](./Update-BrokerImportedFTA/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the imported file type associations with the specified unique identifier. | true | false |  |
| ExtensionName | Gets only the imported file type associations with the specified extension name. For example, ".txt" or ".png". | false | false |  |
| ContentType | Gets only the imported file type associations with the specified content type (as listed in the Registry). For example, "application/msword". | false | false |  |
| Description | Gets only the imported file type associations with the specified description (as listed in the Registry). For example, "Text Document" or "Microsoft Word text document". | false | false |  |
| DesktopGroupUid | Gets only the file type associations imported from a worker machine belonging to the specified desktop group. | false | false |  |
| Edit | Gets only the imported file type associations with the specified Edit command, that includes both the executable name and path, and any arguments to that executable. | false | false |  |
| EditArguments | Gets only the imported file type associations with the specified arguments to the Edit command. | false | false |  |
| EditExecutableName | Gets only the imported file type associations with the specified executable for the Edit command. | false | false |  |
| HandlerName | Gets only the imported file type associations with the specified handler name (as listed in the Registry). For example, "TXTFILE" or "Word.Document.8". | false | false |  |
| Open | Gets only the imported file type associations with the specified Open command, that includes both the executable name and path, and any  arguments to that executable. | false | false |  |
| OpenArguments | Gets only the imported file type associations with the specified arguments to the Open command. | false | false |  |
| OpenExecutableName | Gets only the imported file type associations with the specified executable for the Open command. | false | false |  |
| PerceivedType | Gets only the imported file type associations with the specified perceived type (as listed in the Registry). For example, "document". | false | false |  |
| Print | Gets only the imported file type associations with the specified Print command. | false | false |  |
| PrintTo | Gets only the imported file type associations with the specified PrintTo command. | false | false |  |
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
This cmdlet does not accept any input from the pipeline.
## Return Values

### Citrix.Broker.Admin.Sdk.Importedfta
One or more ImportedFTA objects are returned as output.
## Examples

### Example 1
```
C:\PS> Get-BrokerImportedFTA
```
#### Description
Invoking this cmdlet with no arguments simply returns all of the imported file type association objects. By default, only the first 250 objects are returned. See the -MaxRecordCount and -Skip parameters for information about modifying this.
### Example 2
```
C:\PS> Get-BrokerImportedFTA -ExtensionName ".txt"
```
#### Description
Retrieves all imported file type associations that have the extension ".txt". Note that because imported file type associations are per-desktop group, multiple instances may be returned.
