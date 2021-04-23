
# Revoke-Hypsecuritygroupegress
Removes an egress rule from a security group.
## Syntax
```
Revoke-HypSecurityGroupEgress [-LiteralPath] <String> -GroupId <String[]> -Protocol <String> [-FromPort <Decimal>] [-ToPort <Decimal>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Revoke-HypSecurityGroupEgress [-LiteralPath] <String> -IPRange <String[]> -Protocol <String> [-FromPort <Decimal>] [-ToPort <Decimal>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
To remove a rule, specify parameters matching an existing rule's values.


## Related Commands

* [Amazon AuthorizeSecurityGroupEgress: http://docs.aws.amazon.com/AWSEC2/latest/APIReference/ApiReference-query-AuthorizeSecurityGroupEgress.html](./Amazon AuthorizeSecurityGroupEgress: http://docs.aws.amazon.com/AWSEC2/latest/APIReference/ApiReference-query-AuthorizeSecurityGroupEgress.html/)
* [IANA protocol numbers: http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml](./IANA protocol numbers: http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml/)
* [Grant-HypSecurityGroupIngress](./Grant-HypSecurityGroupIngress/)
* [Grant-HypSecurityGroupEgress](./Grant-HypSecurityGroupEgress/)
* [Revoke-HypSecurityGroupIngress](./Revoke-HypSecurityGroupIngress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the full XDHyp provider path to the security group, equivalent to the FullPath property of the security group object. The path can specify a security group relative to a hypervisor conection or hosting unit. | true | true (ByValue) |  |
| Protocol | Specifies the protocol name or number. Protocol numbers can be found at: http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml<br>Use -1 to specify all protocols. | true | false |  |
| GroupId | Specifies one or more destination security groups to which traffic will be permitted by this rule. This parameter cannot be specified in conjunction with IPRange. | true | false |  |
| IPRange | Specifies one or more destination CIDR IP address ranges to which traffic will be permitted by this rule. This parameter cannot be specified in conjunction with IPRange. | true | false |  |
| FromPort | The start of the port range for port based protocols. For ICMP this specifies the type number.<br>Use -1 to specify all ICMP types. | false | false | 0 |
| ToPort | The end of the port range for port based protocols. For ICMP this specifies the type number, where -1 can be used to specify all ICMP types. | false | false | 0 |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String
The LiteralPath can be piped in.
## Return Values

### None

## Notes
Security groups cannot be removed in AWS if they are referened by rules from other security groups.<br>    Security groups can be added and removed using the New-Item and Remove-Item cmdlets.
## Examples

### Example 1
```
c:\PS> $Group = New-Item -ItemType SecurityGroup -Path XDHyp:\Connections\AWS -Name MySecurityGroup -Description 'Example group'

          c:\PS> Grant-HypSecurityGroupEgress $Group.FullPath -Protocol '-1' -IPRange '0.0.0.0/0'

          c:\PS> Revoke-HypSecurityGroupEgress $Group.FullPath -Protocol '-1' -IPRange '0.0.0.0/0'

          c:\PS> Remove-Item $Group.FullPath
```
#### Description
Create a security group, grant full egress to anywhere, then revoke access and delete the security group.
