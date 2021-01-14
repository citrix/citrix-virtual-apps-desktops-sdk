
# Set-Brokercatalog
Sets the properties of a catalog.
## Syntax
```
Set-BrokerCatalog [-InputObject] <Catalog[]> [-PassThru] [-Description <String>] [-IsRemotePC <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-ProvisioningSchemeId <Guid>] [-PvsAddress <String>] [-PvsDomain <String>] [-RemotePCHypervisorConnectionUid <Int32>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerCatalog [-Name] <String> [-PassThru] [-Description <String>] [-IsRemotePC <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-ProvisioningSchemeId <Guid>] [-PvsAddress <String>] [-PvsDomain <String>] [-RemotePCHypervisorConnectionUid <Int32>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerCatalog cmdlet sets properties of a catalog or set of catalogs. The catalog can be specified by name, in which case only one catalog can be specified, or one or more catalog instances can be passed to the command either by piping or by using the -InputObject parameter.


## Related Commands

* [Get-BrokerCatalog](./Get-BrokerCatalog/)
* [New-BrokerCatalog](./New-BrokerCatalog/)
* [Remove-BrokerCatalog](./Remove-BrokerCatalog/)
* [Rename-BrokerCatalog](./Rename-BrokerCatalog/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the catalog objects to modify. | true | true (ByValue) |  |
| Name | Identifies the catalog to modify. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Description | Supplies the new value of the Description property. | false | false |  |
| IsRemotePC | Supplies a new value for IsRemotePC.<br>IsRemotePC can only be enabled when:<br>o SessionSupport is SingleSession<br>o MachinesArePhysical is true.<br>IsRemotePC can only be set from true to false when no RemotePCAccount references this catalog, and when no Remote PC relationship exists between this catalog and a desktop group. | false | false |  |
| MinimumFunctionalLevel | The new minimum FunctionalLevel required for machines to work successfully in the catalog. If this is higher than the FunctionalLevel of any machines already in the catalog, they will immediately cease to function.<br>Valid values are L5, L7, L7\_6, L7\_7, L7\_8, L7\_9, L7\_20, L7\_25 | false | false |  |
| ProvisioningSchemeId | Specifies the identity of the MCS provisioning scheme the catalog is associated with (can only be specified for new catalogs with a ProvisioningType of MCS; once set can never be changed). | false | false |  |
| PvsAddress | Supplies the new value of the PvsAddress property. Can only be set if CatalogKind is Pvs or PvsPvd. | false | false |  |
| PvsDomain | Supplies the new value of the PvsDomain property. Can only be set if CatalogKind is PvsPvd. | false | false |  |
| RemotePCHypervisorConnectionUid | Supplies the new hypervisor connection to use for powering on remote PCs in this catalog (only allowed when IsRemotePC is true); this will affect all machines already in the catalog as well as those created later. | false | false |  |
| ZoneUid | Supplies the Zone Uid associated with this catalog. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Catalog
You can pipe the catalogs to be modified to Set-BrokerCatalog.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Catalog
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Catalog object.
## Notes
A catalog's Name property cannot be changed by Set-BrokerCatalog. To rename a catalog use Rename-BrokerCatalog.
## Examples

### Example 1
```
C:\PS> Set-BrokerCatalog -Name "MyCatalog" -Description "New Description"
```
#### Description
This example specifies a catalog by name and sets its description.
### Example 2
```
C:\PS> $permCatalogs = Get-BrokerCatalog -AllocationType Static

C:\PS> Set-BrokerCatalog -InputObject $permCatalogs -Description "Permanently assigned machines"
```
#### Description
This example sets the description for all catalogs with AllocationType 'Static'.
