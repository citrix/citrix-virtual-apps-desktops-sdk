
# Set-Applibisolationgroup
Updates an isolation group in the library
## Syntax
```
Set-AppLibIsolationGroup [-IsolationGroupUid] <Int32> [-Name <String>] [-Description <String>] [-Version <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The isolation group will be updated with the new properties


## Related Commands

* [New-AppLibIsolationGroup](./New-AppLibIsolationGroup/)
* [Remove-AppLibIsolationGroup](./Remove-AppLibIsolationGroup/)
* [Set-AppLibIsolationGroupPackage](./Set-AppLibIsolationGroupPackage/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IsolationGroupUid | The AppLibrary's internal unique identifier of the Isolation Group. | true | true (ByPropertyName) |  |
| Name | The name of the isolation group. | false | true (ByPropertyName) |  |
| Description | The description of the isolation group. | false | true (ByPropertyName) |  |
| Version | The version of the isolation group. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Notes
At least one of the name, description and version parameters must be supplied.
## Examples

### Example 1
```
Set-AppLibIsolationGroup -IsolationGroupUid 58 -Name "MyIsolationGroup"
```
#### Description
Updates only the name for the specified isolation group.
### Example 2
```
Set-AppLibIsolationGroup -IsolationGroupUid 58 -Description "Some description here"
```
#### Description
Updates only the description for the specified isolation group.
### Example 3
```
Set-AppLibIsolationGroup -IsolationGroupUid 58 -Version "1.0.0.1"
```
#### Description
Updates only the version for the specified isolation group.
### Example 4
```
Set-AppLibIsolationGroup -IsolationGroupUid 58 -Name "MyIsolationGroup" -Description "Some description here" -Version "1.0.0.1"
```
#### Description
Updates the name, description and version for the specified isolation group.
