
# Remove-Logoperation
Deletes configuration logs
## Syntax
```
Remove-LogOperation -DatabaseCredentials <PSCredential> [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-IncludeIncomplete] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-LogOperation -UserName <String> [-Password <String>] [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-IncludeIncomplete] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-LogOperation -UserName <String> -SecurePassword <SecureString> [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-IncludeIncomplete] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Remove-LogOperation deletes logs from the Configuration  Logging database. This cmdlet targets high level operation logs for deletion. The associated low level operations logs are deleted as part of this operation via cascade deletion functionality present in the configuration logging database schema.


## Related Commands

* [](.//)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DatabaseCredentials | Specifies the credentials of a database user with permission to delete records from the Configuration Logging database. | true | false |  |
| UserName | Specifies the user name of a database user with permission to delete records from the Configuration Logging database. | true | false |  |
| SecurePassword | Specifies the password a database user, in secure string form, with permission to delete records from the Configuration Logging database. | true | false |  |
| Password | Specifies the password of a database user with permission to delete records from the Configuration Logging database. | false | false |  |
| StartDateRange | Specifies the start time of the earliest high level operation to delete | false | false | DateTime.Min |
| EndDateRange | Specifies the end time of the latest high level operation to delete | false | false | DateTime.UtcNow |
| IncludeIncomplete | Specifies if incomplete high level operations should be deleted. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1
```
C:\PS> Remove-LogOperation  -UserName "DOMAIN\User"  -Password "UserPassword"
```
#### Description
Remove all completed operation logs
### Example 2
```
C:\PS> Remove-LogOperation  -UserName "DOMAIN\User"  -Password "UserPassword" -IncludeIncomplete
```
#### Description
Remove all operations
### Example 3
```
C:\PS> Remove-LogOperation -username "domain\userName" -password "password" -StartDateRange "2013-01-01 12:00:00"  -EndDateRange "2013-01-31 12:00:00"
```
#### Description
Delete logs started on or after "2013-01-01 12:00:00" and completed on or before "2013-01-31 12:00:00"
### Example 4
```
C:\PS> $securePassword = ConvertTo-SecureString -String "UserPassword" -AsPlainText -Force

C:\PS> $credentials    = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList "DOMAIN\UserName", $securePassword

C:\PS> Remove-LogOperation -StartDateRange -DatabaseCredentials $credentials
```
#### Description
Delete logs by supplying database user credentials via a credentials object.
