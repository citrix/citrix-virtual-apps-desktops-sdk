
# Get-Brokeruserzonepreference
Gets user/group accounts with zone preferences configured for this site
## Syntax
```
Get-BrokerUserZonePreference -SID <String> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerUserZonePreference [[-Name] <String>] [-DirectoryContext <String>] [-FullName <String>] [-HomeZoneName <String>] [-HomeZoneUid <Guid>] [-IdentityClaims <String>] [-PrimaryClaim <String>] [-UPN <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieve user/group account details with a home zone preference specified and matching the specified criteria. If no parameters are specified this cmdlet enumerates all account details with associated home zones preferences.

For information about advanced filtering options, see about\_Broker\_Filtering.


### Brokeruserzonepreference Object
The BrokerUserZonePreference object represents a user/group account having an associated home zone preference to be used when launching desktop or application sessions. It contains the following properties:


  * DirectoryContext (System.String) The directory context of a user

  * FullName (System.String) Full name of user/group account.

  * HomeZoneName (System.String) Name of home zone preference associated with user/group account for this site.

  * HomeZoneUid (System.Guid) Home zone preference associated with user/group account for this site.

  * IdentityClaims (System.String) The identity claims of a user

  * Name (System.String) SAM name of user group/account (domain\\user).

  * PrimaryClaim (System.String) The primary identity claim of a user

  * SID (System.String) SID of user/group account.

  * UPN (System.String) UPN of user/group account (user@domain).


## Related Commands

* [New-BrokerUserZonePreference](./New-BrokerUserZonePreference/)
* [Set-BrokerUserZonePreference](./Set-BrokerUserZonePreference/)
* [Remove-BrokerUserZonePreference](./Remove-BrokerUserZonePreference/)
* [Get-BrokerUser](./Get-BrokerUser/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SID | Gets user/group accounts with a home zone preference and the specified SID. | true | false |  |
| Name | Gets user/group accounts with a home zone preference and the specified SAM name (domain\\user). | false | false |  |
| DirectoryContext | Gets the broker user with the specified directory context property value. | false | false |  |
| FullName | Gets user/group accounts with a home zone preference and the specified full name. | false | false |  |
| HomeZoneName | Gets user/group accounts having a home zone preference with the specified name. | false | false |  |
| HomeZoneUid | Gets user/group accounts having a home zone preference with the specified UID. | false | false |  |
| IdentityClaims | Gets the broker user with the specified identity claims property value. | false | false |  |
| PrimaryClaim | Gets the broker user with the specified primary claim property value. | false | false |  |
| UPN | Gets user/group accounts with a home zone preference and the specified UPN (user@domain). | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Userzonepreference
Get-BrokerUserZonePreference returns an object for each user/group account with a home zone preference.
## Examples

### Example 1
```
Get-BrokerUserZonePreference DOMAIN7\\*
```
#### Description
Get all user/group accounts with a home zone preference whose names match the supplied pattern
### Example 2
```
Get-BrokerUserZonePreference -HomeZoneUid 79AD8059-05B7-4BAA-9369-5C74EF52D3EB
```
#### Description
Get all user/group accounts with the specified zone as their home zone preference.
