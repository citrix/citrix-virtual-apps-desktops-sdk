
# Get-Applibisolationgroup
Gets the details of an isolation group held in the application library.
## Syntax
```
Get-AppLibIsolationGroup [[-IsolationGroupUid] <Int32>] [-IncludePolicy <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Get-AppLibIsolationGroup [[-Name] <String>] [-IncludePolicy <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The application library holds the information about isolation groups, their location on the network and the packages they contain.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IsolationGroupUid | The App Library's internal unique identifier of the isolation group. | false | true (ByPropertyName) |  |
| Name | The name of the isolation group to fetch. | false | true (ByPropertyName) |  |
| IncludePolicy | The option to retrieve the Isolation Group policy. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Isolationgroup
An object representing the details needed to identify an isolation group.
## Notes
Pass in the isolation group's uid to retreive a single isolation group.<br>    Pass in a library uid to retrieve all of the isolation groups in that library.<br>    Call the cmdlet without any parameters to retieve all of the isolation groups in the AppLibrary.
## Examples

### Example 1
```
Get-AppLibIsolationGroup
```
#### Description
Gets the details for all of the isolation groups in the AppLibrary.
### Example 2
```
Get-AppLibIsolationGroup -Name "MyIsolationGroup"
```
#### Description
Gets the details of the isolation group named MyIsolationGroup.
### Example 3
```
Get-AppLibIsolationGroup -IsolationGroupUid 5
```
#### Description
Gets the details for the isolation with a Uid of 5.
### Example 4
```
Get-AppLibIsolationGroup -IsolationGroupUid 5 -IncludePolicy $true
```
#### Description
Gets the details for the isolation with a Uid of 5 and also returns the Citrix Group Policy data that defines the object.
