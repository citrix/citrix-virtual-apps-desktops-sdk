
# Set-Applibappdnaconnection
Sets the connection details for integration of AppDNA into AppLibrary to allow AppDNA Analysis by this site.
## Syntax
```
Set-AppLibAppDNAConnection [-Address] <String> -Database <String> -UserName <String> -Password <SecureString> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Sets the connection details for integration of AppDNA into AppLibrary to allow AppDNA Analysis of AppDisk, Machines and DesktopGroups.


## Related Commands

* [Get-AppLibAppDNAConnection](./Get-AppLibAppDNAConnection/)
* [Remove-AppLibAppDNAConnection](./Remove-AppLibAppDNAConnection/)
* [Enable-AppLibAppDNAConnection](./Enable-AppLibAppDNAConnection/)
* [Deisable-AppLibAppDNAConnection](./Deisable-AppLibAppDNAConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Address | The URL to the AppDNA web server. | true | false |  |
| Database | The AppDNA database identifier. | true | false |  |
| UserName | The username of the AppDNA user to connect with. | true | false |  |
| Password | The AppDNA user's password | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### String

### System.Security.Securestring
The secure string representing the user's password.
## Return Values

### Citrix.Applibrary.Sdk.Appdnaconnection
This object provides details of the AppDNA Connection and contains the following information:<br>                    Address &lt;string&gt;<br>                    The URL of the AppDNA web server.<br>                    Database &lt;string&gt;<br>                    The database identifier from the AppDNA site<br>                    Enabled &lt;bool&gt;<br>                    Whether or not the connection is enabled<br>                    Username &lt;string&gt;<br>                    The user account name used to make the connection.
## Notes
The AppDNA user's password is stored securely and is never returned in the AppDNAConnection object.<br>    Only one AppDNA configuration can be stored. If a connection is already set up, the connection details will be replaced.<br>    The connection will be enabled by default in the AppLibrary when the details are set.
## Examples

### Example 1
```
C:\PS>$SecurePassword = ConvertTo-SecureString -String "password" -AsPlainText -Force

                    C:\PS>Set-AppLibAppDNAConnection -Address "http://my.appdna.server:8199/AppDNA" -Database "localhost:AppDNADB" -userName "AppDNAUser" -password $SecurePassword

                    Address  : http://my.appdna.server:8199/AppDNA

                    Database : localhost:AppDNADB

                    Enabled  : True

                    UserName : AppDNAUser
```
#### Description
Sets the AppLibrary AppDNA connection to the configuration localhost:AppDNADB on my.appdna.server under the "AppDNAUser" account.
