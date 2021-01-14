
# Set-Applibserviceconfigurationdata
Sets the value for the given key in the service configuration data.
## Syntax
```
Set-AppLibServiceConfigurationData [-Name] <String> -Value <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability for additional custom data to be stored for the AppLibrary Service.


## Related Commands

* [Remove-AppLibServiceConfigurationData](./Remove-AppLibServiceConfigurationData/)
* [Get-AppLibServiceConfigurationData](./Get-AppLibServiceConfigurationData/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the key name of the metadata to be added.  The key must be unique.<br>The Name cannot contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | false |  |
| Value | Specifies the value for the name.  If the name already exists, its value is updated. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Serviceconfigurationdata
Set-AppLibServiceConfigurationData returns an object containing the new definition of the configuration.<br>    Name &lt;string&gt;<br>        Specifies the name for the item of data.<br>    Value &lt;string&gt;<br>        Specifies the value of the data.
## Notes
In the case of failure the following errors can be produced.<br>    Error Codes<br>    -----------<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        An error occurred while communicating with the service.<br>    ExceptionThrown<br>        An unexpected error occurred.  To locate more details see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Set-AppLibServiceConfigurationData -Name "customProperty1" -Value "value2"

Name                            Value

--------                        -----

customProperty1                 value2
```
#### Description
Set data with a name of 'customProperty1' and value of 'value2' to the service configuration.
