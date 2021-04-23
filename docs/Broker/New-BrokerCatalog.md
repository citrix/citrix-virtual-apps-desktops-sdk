
# New-Brokercatalog
Adds a new catalog to the site.
## Syntax
```
New-BrokerCatalog [-Name] <String> [-AllocationType] <AllocationType> [-CatalogKind] <CatalogKind> [-PvsForVM <String[]>] [-Description <String>] [-IsRemotePC <Boolean>] [-MachinesArePhysical <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-PvsAddress <String>] [-PvsDomain <String>] [-RemotePCHypervisorConnectionUid <Int32>] [-Scope <String[]>] [-TenantId <Guid>] [-UUID <Guid>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerCatalog [-Name] <String> [-AllocationType] <AllocationType> [-ProvisioningType] <ProvisioningType> [-SessionSupport] <SessionSupport> [-PersistUserChanges] <PersistUserChanges> [-ProvisioningSchemeId <Guid>] [-Description <String>] [-IsRemotePC <Boolean>] [-MachinesArePhysical <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-PvsAddress <String>] [-PvsDomain <String>] [-RemotePCHypervisorConnectionUid <Int32>] [-Scope <String[]>] [-TenantId <Guid>] [-UUID <Guid>] [-ZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
New-BrokerCatalog adds a catalog through which machines can be provided to the site.

In order for a machine to register in a site, the machine must belong to a catalog with which it is compatible. The compatibility of a machine with a catalog is determined by two of the parameters of New-BrokerCatalog:



* MinimalFunctionalLevel: The minimal functional level supported in the catalog. The functional level of the machine is determined by the capabilities of the Citrix VDA software on it.
* SessionSupport: The session support (single/multi) of the catalog. The session support of the machine is determined by the variant of the Citrix VDA software installed (workstation/terminal services, respectively).


## Related Commands

* [Get-BrokerCatalog](./Get-BrokerCatalog/)
* [Rename-BrokerCatalog](./Rename-BrokerCatalog/)
* [Remove-BrokerCatalog](./Remove-BrokerCatalog/)
* [Set-BrokerCatalog](./Set-BrokerCatalog/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies a name for the catalog. Each catalog within a site must have a unique name. | true | true (ByPropertyName) |  |
| AllocationType | Specifies how machines in the catalog are assigned to users. Values can be:<br>o Static - Machines in a catalog of this type are permanently assigned to a user.<br>o Permanent - equivalent to 'Static'.<br>o Random  - Machines in a catalog of this type are picked at random and temporarily assigned to a user. | true | true (ByPropertyName) |  |
| CatalogKind | Deprecated: The type of machines the catalog will contain. Values can be: ThinCloned, SingleImage, PowerManaged, Unmanaged, Pvs, Pvd or PvsPvd.<br>Thin-Cloned, Single-Image and Personal vDisk Catalogs<br>-----------------------------------------------------<br>Thin-cloned and single-image catalog kinds are for machines created and managed with Provisioning Services for VMs. All machines in this type of catalog are managed, and so must be associated with a hypervisor connection.<br>A thin-cloned catalog is used for original golden VM images that are cloned when they are assigned to a VM, and users' changes to the VM image are retained after the VM is restarted.<br>A single-image catalog is used when multiple machines provisioned with Provisioning Services for VMs all share a single golden VM image when they run and, when restarted, they revert to the original VM image state.<br>A personal vDisk catalog is similar to a single-image catalog, but it also uses personal vDisk technology.<br>PowerManaged<br>------------<br>This catalog kind is for managed machines that are manually provisioned by administrators. All machines in this type of catalog are managed, and so must be associated with a hypervisor connection.<br>Unmanaged<br>---------<br>This catalog kind is for unmanaged machines, so there is no associated hypervisor connection.<br>PVS<br>---<br>This catalog kind is for managed machines that are provisioned using Provisioning Services. All machines in this type of catalog are managed, and so must be associated with a hypervisor connection. Only shared desktops are suitable for this catalog kind.<br>A Provisioning Services-personal vDisk (PvsPvd) catalog is similar to a Provisioning Services catalog, but it also uses personal vDisk technology. | true | true (ByPropertyName) |  |
| ProvisioningType | Specifies the ProvisioningType for the catalog. Values can be:<br>o Manual - No provisioning.<br>o PVS -  Machine provisioned by PVS (machine may be physical, blade, VM,...).<br>o MCS - Machine provisioned by MCS (machine must be VM). | true | true (ByPropertyName) |  |
| SessionSupport | Specifies whether machines in the catalog are single or multi-session capable. Values can be:<br>o SingleSession - Single-session only machine.<br>o MultiSession  - Multi-session capable machine. | true | true (ByPropertyName) |  |
| PersistUserChanges | Specifies how user changes are persisted on machines in the catalog. Possible values are:<br>o OnLocal: User changes are stored on the machine's local storage.<br>o Discard: User changes are discarded.<br>o OnPvd: User changes are stored on the user's personal vDisk. | true | true (ByPropertyName) |  |
| PvsForVM | Deprecated:<br>Identifies the provisioning scheme used by this catalog. To be specified in the format: ProvisioningSchemeGuid:ServiceGroupGuid. Applicable only to thin-cloned, single-image or personal vDisk catalogs. | false | true (ByPropertyName) |  |
| Description | A description for the catalog. | false | true (ByPropertyName) |  |
| IsRemotePC | Specifies whether this is to be a Remote PC catalog.<br>IsRemotePC can only be enabled when:<br>o SessionSupport is SingleSession<br>o MachinesArePhysical is true. | false | true (ByPropertyName) | false |
| MachinesArePhysical | Specifies whether machines in the catalog can be power-managed by the Citrix Broker Service. Where the Citrix Broker Service cannot control the power state of themachine specify \$true, otherwise \$false. Can only be specified together with a provisioning type of Pvs or Manual, or if used with the legacy CatalogKind parameter only with Pvs or PvsPvd catalog kinds. | false | true (ByPropertyName) |  |
| MinimumFunctionalLevel | The minimum FunctionalLevel required for machines to register in the site.<br>Valid values are L5, L7, L7\_6, L7\_7, L7\_8, L7\_9, L7\_20, L7\_25 | false | true (ByPropertyName) | The FunctionalLevel of the current release (L7\_6); by default no machines with less than the most current FunctionalLevel will be functional. |
| PvsAddress | Specifies the URL of the Provisioning Services server. Only applicable to Provisioning Services or Provisioning Services-personal vDisk catalogs. | false | true (ByPropertyName) |  |
| PvsDomain | Specifies the Active Directory domain of the Provisioning Services server. Only applicable to Provisioning Services or Provisioning Services-personal vDisk catalogs. | false | true (ByPropertyName) |  |
| RemotePCHypervisorConnectionUid | Specifies the hypervisor connection to use for powering on remote PCs in this catalog (only allowed when IsRemotePC is true). | false | true (ByPropertyName) |  |
| Scope | Specifies the name of the delegated administration scope to which the catalog belongs. | false | true (ByPropertyName) |  |
| TenantId | Specifies identity of tenant associated with catalog. Must always be specified in multitenant sites, must not be specified otherwise. | false | true (ByPropertyName) |  |
| UUID | An optional GUID for this catalog. | false | true (ByPropertyName) | A new GUID is generated if none is supplied. |
| ZoneUid | Zone Uid associated with this catalog. | false | true (ByPropertyName) | If no Uid is provided the catalog is associated with Primary Zone. |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| ProvisioningSchemeId | Specifies the identity of the MCS provisioning scheme the new catalog is associated with (can only be specified for new catalogs with a ProvisioningType of MCS). | false | true (ByPropertyName) | \$null |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Catalog
New-BrokerCatalog returns the created catalog.
## Examples

### Example 1
```
C:\PS> New-BrokerCatalog -AllocationType Static -CatalogKind Unmanaged -Description "Catalog1 Description" -Name "Catalog1 Name"
```
#### Description
This command creates a catalog that can contain unmanaged physical or virtual machines that are permanently assigned to the user.
### Example 2
```
C:\PS> New-BrokerCatalog -AllocationType Random -CatalogKind PowerManaged -Description "catalog 2 Description" -Name "Catalog2 Name"
```
#### Description
This command creates a catalog that can contain power-managed machines that are randomly assigned to the user.
### Example 3
```
C:\PS> New-BrokerCatalog -AllocationType Random -CatalogKind PVS -Description "PVS Catalog Desc" -Name "PVS Catalog Name" -PvsAddress "pvsServer@pvsDomain.com" -PvsDomain "pvsDomain.com" -PvsForVM $($farmGuid:$schemeGuid)
```
#### Description
This command creates a catalog that can contain managed machines that are provisioned using Provisioning Services.
