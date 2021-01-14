
# Add-Hyphostingunitnetwork
Makes additional hypervisor networks available for use in a HostingUnit.
## Syntax
```
Add-HypHostingUnitNetwork [-LiteralPath] <String> [-NetworkPath] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to extend the set of hypervisor networks that are made available through the HostingUnit to the Citrix Machine Creation Service. When new machines are created, their virtual NICs can be associated only with networks that are in this set. This command cannot be used if the connection for the hosting unit is in maintenance mode.


## Related Commands

* [New-Item](./New-Item/)
* [Add-HypMetadata](./Add-HypMetadata/)
* [remove-HypHostingUnitNetwork](./remove-HypHostingUnitNetwork/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path to the hosting unit to which the network will be added. The path must be in one of the following formats: &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt; or  &lt;drive&gt;:\\HostingUnits\\{&lt;HostingUnit Uid&gt;} | true | false |  |
| NetworkPath | Specifies the path to the network that will be added. The path must be in one of the following formats: &lt;drive&gt;:\\Connections\\&lt;ConnectionName&gt;\\MyNetwork.network or  &lt;drive&gt;:\\Connections\\{&lt;Connection Uid&gt;}\\MyNetwork.network or  &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnitName&gt;\\MyNetwork.network or  &lt;drive&gt;:\\HostingUnits\\{&lt;hostingUnit Uid&gt;}\\MyNetwork.network | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. This can be a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String<br>    You Can Pipe A String That Contains A Path To Add-Hyphostingunitnetwork (Networkpath Parameter).

## Return Values

### Citrix.Host.Sdk.Hostingunit
Add-HypHostingUnitNetwork returns an object containing the new definition of the hosting unit.<br>    HostingUnitUid &lt;Guid&gt;<br>        Specifies the unique identifier for the hosting unit.<br>    HostingUnitName &lt;string&gt;<br>        Specifies the name of the hosting unit.<br>    HypervisorConnection &lt;Citrix.Host.Sdk.HypervisorConnection&gt;<br>        Specifies the connection that the hosting unit uses to access a hypervisor.<br>    RootId &lt;string&gt;<br>        Identifies, to the hypervisor, the root of the hosting unit.<br>    RootPath &lt;string&gt;<br>        The hosting unit provider path that represents the root of the hosting unit.<br>    Storage &lt;Citrix.Host.Sdk.Storage\[\]&gt;<br>        The list of storage items that the hosting unit can use.<br>    PersonalvDiskStorage &lt;Citrix.XDPowerShell.Storage\[\]&gt;<br>        The list of storage items that the hosting unit can use for storing personal data.<br>    VMTaggingEnabled &lt;Boolean&gt;<br>        Specifies whether or not the metadata in the hypervisor can be used to store information about the XenDesktop Machine Creation Service.<br>    NetworkId &lt;string&gt;<br>        The hypervisor's internal identifier that represents the default network specified for the hosting unit.<br>    NetworkPath &lt;string&gt;<br>        The hosting unit provider path to the default network specified for the hosting unit.<br>    Metadata &lt;Citrix.Host.Sdk.Metadata\[\]&gt;<br>        A list of key value pairs that can store additional information about the hosting unit.<br>    PermittedNetworks &lt;Citrix.Host.Sdk.Network\[\]&gt;<br>        A full list of the hypervisor networks that are exposed for use in the hosting unit.
## Notes
The network path must be valid for the hosting unit. The rules that are applied are as follows: XenServer (HypervisorConnection Type = XenServer)<br>    NA<br>    VMWare vSphere/ESX (HypervisorConnection Type = vCenter)<br>    The network path must be directly contained in the root path item of the hosting unit.<br>    Microsoft SCVMM/Hyper-v (HypervisorConnection Type = SCVMM)<br>    NA<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    HostingUnitsPathInvalid<br>    The path provided is not to an item in a subdirectory of a hosting unit item.<br>    HostingUnitNetworkPathInvalid<br>    The specified path is invalid.<br>    HostingUnitNetworkPathInvalid<br>    The network path cannot be found or is invalid. See notes above about validity.<br>    HostingUnitNetworkDuplicateObjectExists<br>    The specified network path is already part of the hosting unit.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Add-HypHostingUnitNetwork -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -NetworkPath 'XDHyp:\HostingUnits\MyHostingUnits\newNetwork.network'

          HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457

          HostingUnitName      : MyHostingUnit

          HypervisorConnection : MyConnection

          RootPath             : /

          RootId               :

          NetworkPath          : /Network 0.network

          NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1

          Storage              : {/Local storage.storage}

          PersonalvDiskStorage : {}

          VMTaggingEnabled     : True

          Metadata             : {}

          PermittedNetworks    : {/Network 0.network, /newNetwork.network}
```
#### Description
The command adds a new network called "newNetwork.network" to the hosting unit called "MyHostingUnit".
### Example 2
```
XDHyp:\HostingUnits\MyHostingUnit>Add-HypHostingUnitNetwork -LiteralPath . -NetworkPath 'XDHyp:\HostingUnits\MyHostingUnits\newNetwork.network'

          HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457

          HostingUnitName      : MyHostingUnit

          HypervisorConnection : MyConnection

          RootPath             : /

          RootId               :

          NetworkPath          : /Network 0.network

          NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1

          Storage              : {/Local storage.storage}

          PersonalvDiskStorage : {}

          VMTaggingEnabled     : True

          Metadata             : {}

          PermittedNetworks    : {/Network 0.network, /newNetwork.network}
```
#### Description
The command adds a new network called "newNetwork.network" to the current directory. The dot (.) represents the current location (not its contents).
### Example 3
```
XDHyp:\HostingUnits\MyHostingUnit>dir \*.network | Add-HypHostingUnitNetwork -LiteralPath XDHyp:\HostingUnits\MyHostingUnit
```
#### Description
The command adds all of the networks that are available in the hosting unit to the specified hosting unit.
### Example 4
```
c:\PS>Add-HypHostingUnitNetwork -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -NetworkPath 'XDHyp:\HostingUnits\MyHostingUnits\newNetwork.network'

          HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457

          HostingUnitName      : MyHostingUnit

          HypervisorConnection : MyConnection

          RootPath             : /

          RootId               :

          NetworkPath          : /Network 0.network

          NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1

          Storage              : {/Local storage.storage}

          PersonalvDiskStorage : {}

          VMTaggingEnabled     : True

          Metadata             : {}

          PermittedNetworks    : {/Network 0.network, /newNetwork.network}
```
#### Description
The command adds a new network location called "newNetwork.network" to the hosting unit called "MyHostingUnit".
