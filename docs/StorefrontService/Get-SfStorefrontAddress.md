
# Get-Sfstorefrontaddress
Gets the high-level description of a configuration for StoreFront addresses, based on a configuration byte array.
## Syntax
```
Get-SfStorefrontAddress [-ByteArray] <Byte[]> [<CommonParameters>]
```
## Detailed Description
Use this command to convert a configuration byte array into a set of named property settings. The byte array will either have been retrieved from the Citrix Broker Service, or from the New-SfStorefrontAddress cmdlet.


## Related Commands

* [New-SfStorefrontAddress](./New-SfStorefrontAddress/)
* [Add-SfStorefrontAddress](./Add-SfStorefrontAddress/)
* [New-BrokerMachineConfiguration](./New-BrokerMachineConfiguration/)
* [Add-BrokerMachineConfiguration](./Add-BrokerMachineConfiguration/)
* [Set-BrokerMachineConfiguration](./Set-BrokerMachineConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ByteArray | Specifies the low-level byte array (blob) to be interpreted. | true | true (ByValue) |  |

## Input Type

### System.Byte\[\]
The cmdlet accepts the ByteArray parameter as pipeline input.
## Return Values

### Citrix.Storefront.Sdk.Sfstorefrontaddress
This cmdlet outputs one SfStorefrontAddress object for each address that is configured within the slot. Each object has the following properties:<br>Name - Specifies the name of the StoreFront.<br>Url - Specifies the URL to the StoreFront, such as "https://mysite.com/Citrix/StoreWeb".<br>Enabled - Specifies whether the StoreFront is enabled for users.<br>Description - Specifies the human-readable name of the StoreFront.
## Examples

### Example 1
```
C:\PS> $configuration = New-SfStorefrontAddress -Url "https://mysite.com/Citrix/StoreWeb" -Description "This StoreFront delivers my corporate applications" -Name "StoreFront1" -Enabled $true

C:\PS> Get-SfStorefrontAddress -ByteArray $configuration

Name               Url                                       Enabled Description

----               ---                                       ------- -----------

StoreFront1        https://mysite.com/Citrix/StoreWeb           True This StoreFront delivers my corporate applications.
```
#### Description
This example shows a new configuration byte array being created to specify a single StoreFront address. The configuration byte array is then provided as input to the Get-SfStorefrontAddress command, which interprets and outputs the same fields.
