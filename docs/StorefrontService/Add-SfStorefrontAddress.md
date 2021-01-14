
# Add-Sfstorefrontaddress
Modifies a StoreFront address configuration by adding an additional StoreFront address to it.
## Syntax
```
Add-SfStorefrontAddress [-ByteArray] <Byte[]> -Name <String> -Url <String> -Enabled <Boolean> -Description <String> [<CommonParameters>]
```
## Detailed Description
Use this command to transform an existing StoreFront configuration into a new configuration, where the new configuration contains one additional address. The original configuration is supplied as an input, along with the properties of the new StoreFront address being added. The cmdlet outputs the modified configuration, which can then be passed to the Citrix Broker Service using the Add-BrokerMachineConfiguration command.


This command does not, by itself, have any persistent effects within XenDesktop. To make the change persistent, the new configuration byte array must first be transformed into a machine configuration within the Citrix Broker Service. To do this, use the New-BrokerMachineConfiguration command. You can then use the Add-BrokerMachineConfiguration and Set-BrokerMachineConfiguration commands to fully associate the new configuration with a delivery group.


## Related Commands

* [New-SfStorefrontAddress](./New-SfStorefrontAddress/)
* [Get-SfStorefrontAddress](./Get-SfStorefrontAddress/)
* [New-BrokerMachineConfiguration](./New-BrokerMachineConfiguration/)
* [Add-BrokerMachineConfiguration](./Add-BrokerMachineConfiguration/)
* [Set-BrokerMachineConfiguration](./Set-BrokerMachineConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ByteArray | Specifies the initial configuration, on which the new configuration is based. All of the addresses in the original configuration are also present in the new configuration, along with the additional address specified. This configuration byte array is obtained from an earlier call to New-SfStorefrontAddress, or from Get-BrokerMachineConfiguration. | true | true (ByValue) |  |
| Name | Specifies the name of the new StoreFront. | true | false |  |
| Url | Specifies the URL to the StoreFront, such as "https://mysite.com/Citrix/StoreWeb". | true | false |  |
| Enabled | Specifies if the new StoreFront address should be enabled for user access. | true | false |  |
| Description | Specifies a human-readable description of the new StoreFront. | true | false |  |

## Input Type

### System.Byte\[\]
This cmdlet accepts configurations as pipeline input, as an alternative to supplying the ByteArray parameter.
## Return Values

### System.Byte\[\]
This cmdlet outputs the new, modified configuration. This differs from the original configuration in that it contains the additional StoreFront address.
## Examples

### Example 1
```
C:\PS> $newConfiguration = Add-SfStorefrontAddress -ByteArray $originalConfiguration -Url "https://mysite.com/Citrix/StoreWeb" -Description "This StoreFront delivers my corporate applications" -Name "StoreFront1" -Enabled $true
```
#### Description
This command transforms the configuration byte array specified by \$originalConfiguration, adds the new StoreFront details, and stores the resulting configuration in \$newConfiguration.
