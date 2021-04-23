
# Get-Applibappvapplicationspolicy
Gets the updated policy for the list of applications passed
## Syntax
```
Get-AppLibAppVApplicationsPolicy [[-AppIdentifierList] <String[]>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet should be used to get policy for published single admin App-V applications. The input should be a list of App-V application identifiers list


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppIdentifierList | List of App-V application identifiers | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Byte\[\]
byte array containing the updated policy
## Notes
Pass in the App Identifiers as a comma separated string
## Examples

### Example 1
```
$appIdentifiers = "4345-fr23320-df","45234-sdewr-gfgf","785ddf-vcvxdsf-dfdf"

          Get-AppLibAppVApplicationsPolicy -AppIdentifierList $appIdentifiers
```
#### Description
Gets the updated policy for the list of applications passed
