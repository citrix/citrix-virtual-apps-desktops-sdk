
# Stop-Loghighleveloperation
Logs the completion of a previously started high level operation.
## Syntax
```
Stop-LogHighLevelOperation -HighLevelOperationId <String> -IsSuccessful <Boolean> [-EndTime <DateTime>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Stop-LogHighLevelOperation logs the completion of a started high level operation.


## Related Commands

* [Start-LogHighLevelOperation](./Start-LogHighLevelOperation/)
* [Get-LogHighLevelOperation](./Get-LogHighLevelOperation/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| HighLevelOperationId | Specifies the identifier of the high level operation being completed. | true | false |  |
| IsSuccessful | Specifies if the started high level operation completed sucessfully. | true | false |  |
| EndTime | Specifies the end time of the high level operation being completed. | false | false | DateTime.UtcNow. |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1
```
C:\PS> $succeeded = $false #indicates if high level operation succeeded.

C:\PS> # Log high level operation start.

C:\PS> $highLevelOp = Start-LogHighLevelOperation -Text "Create unmanaged catalog" -Source "My Custom Script"

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
