
# Test-Applibappdnaconnection
Tests AppDNA connection.
## Syntax
```
Test-AppLibAppDNAConnection [-Address] <String> -Database <String> -UserName <String> -Password <SecureString> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Tests whether a connection to the configured AppDNA server can be made.


## Related Commands

* [Set-AppLibAppDNAConnection](./Set-AppLibAppDNAConnection/)
* [Remove-AppLibAppDNAConnection](./Remove-AppLibAppDNAConnection/)
* [Enable-AppLibAppDNAConnection](./Enable-AppLibAppDNAConnection/)
* [Enable-AppLibAppDNAConnection](./Enable-AppLibAppDNAConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Address | The URL to the AppDNA web server. | true | false |  |
| Database | The AppDNA database identifier. | true | false |  |
| UserName | The username of the AppDNA user to connect with. | true | false |  |
| Password | The AppDNA user's password. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### String

### System.Security.Securestring
The secure string representing the users password.
## Return Values

### Bool

## Examples

### Example 1
```
C:\PS>$SecurePassword =  ConvertTo-SecureString -String "passord" -AsPlainText -Force

                    C:\PS>Set-AppLibAppDNAConnection -Address "http://AppDNAServer.mydomain.net:8199/AppDNA" -Database "AppDNAServer:AppDNADB" -userName "AppDNAUser" -paassword $SecurePassword

                    True
```
#### Description
Tests whether a connection to be made to an AppDNA server with the credentials provided. In this example the connection was successful.
### Example 2
```
C:\PS>$SecurePassword =  ConvertTo-SecureString -String "passord" -AsPlainText -Force

                    C:\PS>Set-AppLibAppDNAConnection -Address "http://AppDNAServer.mydomain.net:8199/AppDNA" -Database "AppDNAServer:AppDNADB" -userName "AppDNAUser" -paassword $SecurePassword

                    False

                    Test-AppLibAppDNAConnection : An exception occurred.  The associated message was Unable to connect to the remote server

                    At line:1 char:1

                    + Test-AppLibAppDNAConnection -Address "http://AppDNAServer.mynetwork.net:8199/App ...

                    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

                    + CategoryInfo          : InvalidOperation: (:) [Test-AppLibAppDNAConnection], InvalidOperationException

                    + FullyQualifiedErrorId : Citrix.XDPowerShell.Status.ExceptionThrown,Citrix.AppLibrary.Sdk.Commands.TestAppLibAppDNAConnectionCommand
```
#### Description
Tests whether a connection to be made to an AppDNA server with the credentials provided. In this example the connection was not successful.
