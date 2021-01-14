
# New-Sfstorefrontaddress
Creates a new StoreFront address configuration, specifying a single address.
## Syntax
```
New-SfStorefrontAddress -Name <String> -Url <String> -Enabled <Boolean> -Description <String> [<CommonParameters>]
```
## Detailed Description
Use this command when you want to create a new StoreFront configuration byte array from scratch, rather than modifying an existing one. You must define the URL for the StoreFront, and some additional details.


This command does not, by itself, have any persistent effects within XenDesktop. To make the change persistent, the new configuration byte array must first be transformed into a machine configuration within the Citrix Broker Service. To do this, use the New-BrokerMachineConfiguration command. You can then use the Add-BrokerMachineConfiguration and Set-BrokerMachineConfiguration commands to fully associate the new configuration with a delivery group.


## Related Commands

* [Add-SfStorefrontAddress](./Add-SfStorefrontAddress/)
* [Get-SfStorefrontAddress](./Get-SfStorefrontAddress/)
* [New-BrokerMachineConfiguration](./New-BrokerMachineConfiguration/)
* [Add-BrokerMachineConfiguration](./Add-BrokerMachineConfiguration/)
* [Set-BrokerMachineConfiguration](./Set-BrokerMachineConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the name of the new StoreFront. | true | false |  |
| Url | Specifies the URL to the StoreFront, such as "https://mysite.com/Citrix/StoreWeb". | true | false |  |
| Enabled | Specifies if the new StoreFront address should be enabled for user access. | true | false |  |
| Description | Specifies a human-readable description of the new StoreFront. | true | false |  |

## Input Type

### None

## Return Values

### System.Byte\[\]
The new configuration set, with all of the given modifications applied.
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
