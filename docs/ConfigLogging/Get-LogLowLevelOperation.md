
# Get-Loglowleveloperation
Gets low level operations
## Syntax
```
Get-LogLowLevelOperation [-Id <Guid>] [-HighLevelOperationId <Guid>] [-StartTime <DateTime>] [-EndTime <DateTime>] [-IsSuccessful <Boolean>] [-User <String>] [-AdminMachineIP <String>] [-Text <String>] [-Source <String>] [-SourceSdk <String>] [-OperationType <OperationType>] [-TargetType <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves low level operations matching the specified criteria. If no parameters are specified this cmdlet returns all low level operations.


## Related Commands

* [Get-LogLowLevelOperation](./Get-LogLowLevelOperation/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Id | Gets the low level operation with the specified identifier. | false | true (ByPropertyName) |  |
| HighLevelOperationId | Gets low level operations for the high level operation with the specified identifier. | false | false |  |
| StartTime | Gets low level operations with the specified start time | false | false |  |
| EndTime | Gets low level operations with the specified end time. | false | false |  |
| IsSuccessful | Gets low level operations with the specified success indicator. | false | false |  |
| User | Gets low level operations logged by the specified administrator. | false | false |  |
| AdminMachineIP | Gets low level operations logged from the machine with the specified IP address. | false | false |  |
| Text | Gets low level operations with the specified text | false | false |  |
| Source | Gets low level operations with the specified source. | false | false |  |
| SourceSdk | Gets low level operations logged from the SDK with the specified identifier. | false | false |  |
| OperationType | Gets low level operations with the specified operation type. Values can be:<br>o AdminActivity - to get operations which log administration activity.<br>o ConfigurationChange - to get operations which log configuration changes. | false | false |  |
| TargetType | Gets low level operations with the specified target type. The target type describes the type of object that was the target of the configuration change. For example, "Session" or "Machine". | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Log\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_Log\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Configurationlogging.Sdk.Lowleveloperation
The returned LowLevelOperation object has the following properties:<br>o Id - The unique identifier of the operation.<br>o Text - A description of the operation.<br>o HighLevelOperationId - The unique identifier of the related high level operation.<br>o StartTime - The date and time that the operation started.<br>o EndTime - The date and time that the operation completed. This will be null if the operation is still in progress, or if the operation never completed.<br>o IsSuccessful - Indicates whether the operation completed successfully or not. This will be null if the operation is still in progress, or if the operation never completed.<br>o AdminSid - The identifier of the administrator who performed the operation.<br>o AdminMachineIP - The IP address of the machine that the operation was performed on.<br>o Source - The name of the XenDesktop service that the operation was performed on; for example, "MachineCreation", "DelegatedAdmin".<br>o SourceSdk - The identifier of the XenDesktop service SDK through which the operation was performed; for example, "Prov", "Admin".<br>o OperationType - The operation type. This can be 'AdminActivity' or 'ConfigurationChange'.<br>o TargetTypes - Identifies the type of objects that were affected by the operation. For example, "Catalog" or "Desktop","Machine".<br>o Parameters - The names and values of the parameters that were supplied for the operation.<br>o Details - A collection of OperationDetail objects containing specific information about each object affected by the operation.<br>Each OperationDetail object in the 'Details' collection has the following properties:<br>o TargetUid - The unique identifier of the target object affected by the operation.<br>o TargetName - The name of the target object affected by the operation.<br>o TargetType - The type of the target object.<br>o Text - The description of operation performed on the target object.<br>o StartTime - The date and time that the operation started.<br>o EndTime - The date and time that the operation completed. This will be null if the operation is still in progress, or if the operation never completed.<br>o IsSuccessful - Indicates whether the operation completed successfully or not. This will be null if the operation is still in progress, or if the operation didn't complete.<br>The following properties will be set if the operation changed a property on the object:<br>o PropertyName - The name of the changed property.<br>o NewValue - The new property value.<br>o PreviousValue - The previous property value.<br>o AddValue - If the object property contains a set of values, this specifies the new value which was added to the set.<br>o RemoveValue- If the object property contains a set of values, this specifies the value which was removed from the set.
## Examples

### Example 1
```
C:\PS> Get-LogLowLevelOperation
```
#### Description
Get all low level operations
### Example 2
```
C:\PS> Get-LogLowLevelOperation -OperationType ConfigurationChange
```
#### Description
Get low level operations which log configuration changes.
### Example 3
```
C:\PS> Get-LogLowLevelOperation -OperationType AdminActivity
```
#### Description
Get low level operations which log administration activities.
### Example 4
```
C:\PS> Get-LogLowLevelOperation -Filter{ StartTime -ge "2013-02-27 09:00:00" -and EndTime -le "2013-02-27 18:00:00"}
```
#### Description
Use advanced filtering to get low level operations with a start time on or after "2013-02-27 09:00:00" and an end time on or before "2013-02-27 18:00:00".
### Example 5
```
C:\PS> Get-LogLowLevelOperation -EndTime $null

C:\PS> Get-LogLowLevelOperation -IsSuccessful $null
```
#### Description
Either of these commands will get low level operations which have not yet been completed.
### Example 6
```
C:\PS> Get-LogLowLevelOperation -User "DOMAIN\UserName"
```
#### Description
Get low level operations performed by user "DOMAIN\\UserName".
