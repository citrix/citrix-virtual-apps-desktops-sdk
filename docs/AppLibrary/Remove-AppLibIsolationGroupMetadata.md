
# Remove-Applibisolationgroupmetadata
Removes metadata from the given IsolationGroup.
## Syntax
```
Remove-AppLibIsolationGroupMetadata [-IsolationGroupUid] <Int32> -Name <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AppLibIsolationGroupMetadata [-IsolationGroupUid] <Int32> -Map <PSObject> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AppLibIsolationGroupMetadata [-IsolationGroupName] <String> -Name <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AppLibIsolationGroupMetadata [-IsolationGroupName] <String> -Map <PSObject> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AppLibIsolationGroupMetadata [-InputObject] <IsolationGroup[]> -Name <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AppLibIsolationGroupMetadata [-InputObject] <IsolationGroup[]> -Map <PSObject> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AppLibIsolationGroupMetadata -Map <PSObject> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to remove metadata from the given IsolationGroup.


## Related Commands

* [Set-AppLibIsolationGroupMetadata](./Set-AppLibIsolationGroupMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IsolationGroupUid | Id of the IsolationGroup | true | true (ByValue, ByPropertyName) |  |
| IsolationGroupName | Name of the IsolationGroup | true | true (ByValue, ByPropertyName) |  |
| InputObject | Objects from which the metadata is to be removed. | true | true (ByValue) |  |
| Name | The metadata property to remove. | true | false |  |
| Map | Specifies a dictionary of (name, value)-pairs for the properties. This can be either a hashtable (created with @{"name1" = "val1"; "name2" = "val2"}) or a string dictionary (created with new-object "System.Collections.Generic.Dictionary\[String,String\]"). The properties whose names match keys in the map will be removed. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    InvalidParameterCombination<br>        The cmdlet parameters are inconsistent.<br>    UnknownObject<br>        One of the specified objects was not found.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Remove-AppLibIsolationGroupMetadata -IsolationGroupUid 1 -Name "Custom Data"
```
#### Description
Removes the metadata item named 'Custom Data' from the specified IsolationGroup object.
### Example 2
```
c:\PS>Get-AppLibIsolationGroup | % { Remove-AppLibIsolationGroupMetadata -Map $_.MetadataMap }
```
#### Description
Remove all metadata from all IsolationGroup objects.
