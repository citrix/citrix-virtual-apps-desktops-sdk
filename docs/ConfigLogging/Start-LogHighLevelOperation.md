
# Start-Loghighleveloperation
Logs the start of a high level operation.
## Syntax
```
Start-LogHighLevelOperation -Text <String> -Source <String> [-StartTime <DateTime>] [-OperationType <OperationType>] [-TargetTypes <String[]>] [-Parameters <Hashtable>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Start-LogHighLevelOperation creates a log entry to record the start of a high level operation.

Start-LogHighLevelOperation can be called to log high level configuration changes which originate from customized configuration scripts. Start-LogHighLevelOperation should be called before the script invokes service SDK cmdlets which execute the configuration changes.

Start-LogHighLevelOperation returns a HighLevelOperation object which contains information about the started high level operation. The "Id" property of the returned HighLevelOperation uniquely identifies the started high level operation. This can be supplied into the "-LoggingId" parameter which is implemented in all service SDK cmdlets which execute loggable configuration changes.

High level operation logs are automatically created by the XenDesktop consoles when:

* Initiating an operation which performs configuration changes.
* 
Initiating an operation which performs an administration activity. Configuration Change and Administrator Activity ----------------------------------------------- A configuration change is an operation which alters the configuration of the XenDesktop site. Examples of a configuration changes include:

* Creating or editing a host.
* Creating or editing a catalog.
* Adding a user to a delivery group.
* 
Deleting a machine. An administrator activity operation doesn't directly alter site configuration, but it could be an operation carried out by an administrator as part of site management or helpdesk support. Examples of administrator activities include:

* Shutdown/start/restart of a user desktop.
* Studio or Director sending a message to a user.
* 
Rebooting a user's desktop. Once the change being logged has completed (whether successfully or not) the Stop-LogHighLevelOperation cmdlet should be called to log the completion of a started high level operation.


## Related Commands

* [Stop-LogHighLevelOperation](./Stop-LogHighLevelOperation/)
* [Get-LogHighLevelOperation](./Get-LogHighLevelOperation/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Text | Specifies text to describe the high level operation. | true | false |  |
| Source | Specifies the source of the high level operation. | true | false |  |
| StartTime | Specifies the start time of the high level operation. | false | false | DateTime.UtcNow |
| OperationType | Specifies the type of operation being logged. Values can be:<br>o AdminActivity - If the operation being logged performs an administration activity.<br>o ConfigurationChange - If the operation being logged performs a configuration change. | false | false | ConfigurationChange |
| TargetTypes | Specifies the names of the object types that will be affected by the operation being logged. | false | false |  |
| Parameters | Specifies the names and values of parameters that are supplied to the operation being logged. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Configurationlogging.Sdk.Highleveloperation
The newly logged high level operation start.
## Examples

### Example 1
```
C:\PS> $succeeded = $false #indicates if high level operation succeeded.

C:\PS> # Log high level operation start.

C:\PS> $highLevelOp = Start-LogHighLevelOperation -Text "Create catalog" -Source "My Custom Script"

C:\PS>

C:\PS> try

C:\PS> {

C:\PS>   # Create catalog object

C:\PS>   $catalog = New-BrokerCatalog -Name "MyCatalog" -ProvisioningType Manual -AllocationType Permanent -MinimumFunctionalLevel 'LMAX' -LoggingId $highLevelOp.Id

C:\PS>

C:\PS>   # Add a machine to the catalog

C:\PS>   $machine = New-BrokerMachine -CatalogUid $catalog.Uid -MachineName "DOMAIN\Machine" -LoggingId $highLevelOp.Id

C:\PS>   $succeeded = $true

C:\PS> }

C:\PS> catch{ "Error encountered" }

C:\PS>

C:\PS> finally{

C:\PS>   # Log high level operation stop, and indicate its success

C:\PS>   Stop-LogHighLevelOperation -HighLevelOperationId $highLevelOp.Id -IsSuccessful $succeeded

C:\PS> }
```
#### Description
Creates an unmanaged catalog and assigns a machine to it, within the scope of a high level operation start and stop. The identifier of the high level operation is passed into the "-LoggingId" parameter of the service SDK cmdlets. The execution of the cmdlets in the services will create the low level operation logs for the supplied high level operation.
