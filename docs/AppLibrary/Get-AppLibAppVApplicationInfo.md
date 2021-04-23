
# Get-Applibappvapplicationinfo
Enumerates information for a given application in a given package
## Syntax
```
Get-AppLibAppVApplicationInfo -PackageGuid <String> -ApplicationId <Int32> [-LibraryId <Int32>] [-Property <String[]>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Allows you to query application information about single admin appv package. Currently only fetching filetype associations is supported. See example


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| PackageGuid | The package Guid | true | true (ByPropertyName) |  |
| ApplicationId | The AppV application Id | true | true (ByPropertyName) |  |
| LibraryId | The Application Library Id | false | true (ByPropertyName) |  |
| Property | The property parameter is reserved for future use. Currently only FileTypeAssociations are supported. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Object With Required Information Wihtin Object As Properties

## Notes
Currently only fetching file type associations are supported.
## Examples

### Example 1
```
Get-AppLibAppVApplicationInfo -PackageGuid "7796B8F3-713A-446F-840D-18E5171AB21A" -ApplicationId 14
```
#### Description
Fetches all the file type associations for the given application
