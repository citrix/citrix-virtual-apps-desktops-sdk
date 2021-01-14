
# New-Brokerconfiguredfta
Creates a file type association with a published application.
## Syntax
```
New-BrokerConfiguredFTA -ImportedFTA <ImportedFTA> -ApplicationUid <Int32> [-UUID <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerConfiguredFTA -ExtensionName <String> -HandlerName <String> -ApplicationUid <Int32> [-ContentType <String>] [-HandlerDescription <String>] [-HandlerOpenArguments <String>] [-UUID <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Creates an association between a file type and a published application for the purposes of the content redirection.

File type association associates a file extension (such as ".txt") with an application (such as Notepad). In a Citrix environment file type associations on a user device can be configured so that when an user clicks on a document it launches the appropriate published application. This is known as "content redirection".

Configured file type associations are different from imported file type associations. Configured file type associations are those that are actually associated with published applications for the purposes of content redirection. Imported file type associations are lists of known file type associations for a given desktop group. See Update-BrokerImportedFTA for more information about imported file type associations.

This cmdlet has two parameter sets, which correspond to the cmdlet's two use cases.

The first use case leverages imported file type associations to configure file types for published applications. Information about the file type association is read from the imported object. See the Update-BrokerImportedFTA cmdlet for more information about importing file type associations from a worker machine.

The second use case is more complex and allows you to create your own file type association without having to import it first. This also lets you create custom file type associations that may not already exist on the worker machines. This use case is more error-prone, however, because the individual attributes of the file type association must be correctly specified by you.


## Related Commands

* [Get-BrokerImportedFTA](./Get-BrokerImportedFTA/)
* [Get-BrokerConfiguredFTA](./Get-BrokerConfiguredFTA/)
* [Remove-BrokerConfiguredFTA](./Remove-BrokerConfiguredFTA/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ApplicationUid | Specifies the application with which the file type should be associated. | true | true (ByPropertyName) | (required) |
| ImportedFTA | Specifies the ImportedFTA object to use for creating the ConfiguredFTA object. All values needed to create a ConfiguredFTA object are read from the ImportedFTA object. | true | true (ByPropertyName) | (required) |
| ExtensionName | Specifies the extension name for the file type association. For example, ".txt" or ".doc". | true | true (ByPropertyName) | (required) |
| HandlerName | Specifies the name of the handler for the file type association (as seen in the Registry). For example, "TXTFILE" or "Word.Document.8". | true | true (ByPropertyName) | (required) |
| UUID | An optional GUID for this ConfiguredFTA. | false | false | A new GUID is generated if none is supplied. |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| ContentType | Specifies the content type of the file type (as listed in the Registry). For example, content type would be "text/plain" or "application/msword". | false | true (ByPropertyName) | null |
| HandlerDescription | Specifies the description of the handler for the file type association. | false | true (ByPropertyName) | null |
| HandlerOpenArguments | Specifies the arguments for the open command that the handler should use. For example, "%1". | false | true (ByPropertyName) | null |

## Input Type

### Variable, Based On Property Name.
This cmdlet does accept input from the pipeline but only by property name.
## Return Values

### Citrix.Broker.Admin.Sdk.Configuredfta
This cmdlet returns a single ConfiguredFTA object.
## Examples

### Example 1
```
C:\PS> $app = Get-BrokerApplication "Notepad"

C:\PS> $fta = Get-BrokerImportedFTA -ExtensionName ".txt"

C:\PS> New-BrokerConfiguredFTA -ImportedFTA $fta -ApplicationUid $app.Uid
```
#### Description
Gets the Uid for the application, gets the ImportedFTA object for the file extension, and finally associates ".txt" with the published "Notepad" application.&lt;br&gt;Note that the Get-BrokerImportedFTA cmdlet may return more than one ImportedFTA objects for a specific extension name. See the help for that cmdlet for more details.
### Example 2
```
C:\PS> $app = Get-BrokerApplication "Notepad"

C:\PS> New-BrokerConfiguredFTA -ApplicationUid $app.Uid -ExtensionName ".txt" -HandlerName "txtfile" -ContentType "text\plain" -HandlerDescription "Text Document" -HandlerOpenArguments "%1"
```
#### Description
This example is identical to the first, but shows the the second use case of the cmdlet, specifying each attribute manually.
