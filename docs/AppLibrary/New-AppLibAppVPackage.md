
# New-Applibappvpackage
Adds a new package to the library.
## Syntax
```
New-AppLibAppVPackage -LibraryUid <Int32> -Path <String> [-RetrieveIcon <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AppLibAppVPackage -Path <String> -AppManifestXml <String> -AppManifestIcons <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AppLibAppVPackage -Path <String> -AppManifestXml <String> -AppManifestIcons <String> -ManagementServer <String> -PublishingServer <String> -PackageProperties <String> [-RetrieveIcon <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The package and the applications that make it up are added to the library.


## Related Commands

* [Remove-AppLibAppVPackage](./Remove-AppLibAppVPackage/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LibraryUid | The UID of the library to which the package is added. | true | true (ByPropertyName) |  |
| Path | The full path to the package on the network share. | true | true (ByPropertyName) |  |
| AppManifestXml | The Package's AppManifest Xml | true | false |  |
| AppManifestIcons | A dictionary containing data for icons containied in te package keyed by their path in the AppManifest Xml | true | false |  |
| ManagementServer | Fully qualified domain name of the machine hosting Microsoft App-V Management Server | true | true (ByPropertyName) |  |
| PublishingServer | Url of App-V publishing server | true | true (ByPropertyName) |  |
| PackageProperties | Extracted AppV Package properties | true | true (ByPropertyName) |  |
| RetrieveIcon | A switch to indicate whether to return the package and applications' icon data. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appvpackage
An object representing the details of the the new package.
## Notes
If supplied, the value of the LibraryUid parameter must be 1. No other values are supported.<br>    When a package is added to the library and a record of that package already exists, the existing package is updated with the details of the new package. A package is considered as already existing when the following are true: 1) The PackageGuid and VersionGuid are the same as the existing package and the Path is the same or different. 2) The Path is the same as the existing package and the PackageGuid and/or VersionGuid are the same or different.
## Examples

### Example 1
```
New-AppLibAppVPackage -LibraryUid 1 -Path "\\NetworkStorage.enterprise.com\Managed App-V Packages\Package.appv"
```
#### Description
Adds the package at the specified network location to the library by interrogating the packge file and extrcting the neccesary informaion
### Example 2
```
New-AppLibAppVPackage -Path "\\NetworkStorage.enterprise.com\Managed App-V Packages\Package.appv" -AppManifestXml $AppManifestxml -AppManifestIcons $DictinaryOfIcons
```
#### Description
Adds the package at the specified network location to the library by interpreting only the supplied AppManifest Xml when no physical access to the package is possible.
