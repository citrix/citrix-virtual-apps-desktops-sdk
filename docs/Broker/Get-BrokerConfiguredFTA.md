
# Get-Brokerconfiguredfta
Gets any file type associations configured for an application.
## Syntax
```
Get-BrokerConfiguredFTA -Uid <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerConfiguredFTA [-ApplicationUid <Int32>] [-ContentType <String>] [-ExtensionName <String>] [-HandlerDescription <String>] [-HandlerName <String>] [-HandlerOpenArguments <String>] [-UUID <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Gets any file type associations that are configured for content redirection to a published application.

File type association associates a file extension (such as ".txt") with an application (such as Notepad). In a Citrix environment file type associations on a user device can be configured so that when an user clicks on a document it launches the appropriate published application. This is known as "content redirection".

Configured file type associations are different from imported file type associations. Configured file type associations are those that are actually associated with published applications for the purposes of content redirection. Imported file type associations are lists of known file type associations for a given desktop group. See Update-BrokerImportedFTA for more information about imported file type associations.


### Brokerconfiguredfta Object
The BrokerConfiguredFTA object represents a file type association configured for a published application. It contains the following properties:


  * ApplicationUid (System.Int32) The Uid of the application configured for the file type association.

  * ContentType (System.String) Content type of the file, such as "text/plain" or "application/vnd.ms-excel".

  * ExtensionName (System.String) A single file extension, such as .txt, unique within the scope of a desktop group.

  * HandlerDescription (System.String) File type description, such as "Test Document", "Microsoft Word Text Document", etc.

  * HandlerName (System.String) File type handler name, e.g. "Word.Document.8" or TXTFILE.

  * HandlerOpenArguments (System.String) The arguments used for the ‘open’ action on files of this type.

  * Uid (System.Int32) Unique internal identifier of configured file type association.

  * UUID (System.Guid) UUID of the configured file type association.


## Related Commands

* [New-BrokerConfiguredFTA](./New-BrokerConfiguredFTA/)
* [Remove-BrokerConfiguredFTA](./Remove-BrokerConfiguredFTA/)
* [Update-BrokerImportedFTA](./Update-BrokerImportedFTA/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the configured file type association for the specified unique identifier. | true | false |  |
| ApplicationUid | Gets only the configured file type associations for the specified application unique identifier. | false | false |  |
| ContentType | Gets only the configured file type associations for the specified content type (as seen in the Registry). For example, "text/plain" or "application/msword". | false | false |  |
| ExtensionName | Gets only the configured file type associations for the specified extension name. For example, ".txt" or ".doc". | false | false |  |
| HandlerDescription | Gets only the configured file type associations for the specified handler description. For example, "Text Document". | false | false |  |
| HandlerName | Gets only the configured file type associations for the specified handler name. For example, "TXTFILE" or "Word.Document.8". | false | false |  |
| HandlerOpenArguments | Gets only the configured file type associations for the specified open argument to the handler. For example, "%1". | false | false |  |
| UUID | Gets configured file type associations with the specified value of UUID. | false | false |  |
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
No input is accepted from the pipeline.
## Return Values

### Citrix.Broker.Admin.Sdk.Configuredfta
This cmdlet returns one or more ConfiguredFTA objects.
## Examples

### Example 1
```
C:\PS> Get-BrokerConfiguredFTA
```
#### Description
Returns all configured file type associations.
### Example 2
```
C:\PS> Get-BrokerConfiguredFTA -ExtensionName ".txt"
```
#### Description
Returns only configured file type associations that have a ".txt" extension.
