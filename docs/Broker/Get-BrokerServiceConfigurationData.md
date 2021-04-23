
# Get-Brokerserviceconfigurationdata
View the Service configuration data objects.
## Syntax
```
Get-BrokerServiceConfigurationData -SettingName <String> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerServiceConfigurationData [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
View the Service configuration data objects stored in the broker database. These objects if set correctly, overrride the values present in the windows registry


### Brokerserviceconfigurationdata Object
The service configuration object. It is a key value pair that can be used to tweek some settings in the broker


  * SettingName (System.String) Name of the ServiceConfigurationData setting

  * SettingValue (System.String) Value of the ServiceConfigurationData setting. Note that it need to be in the permissible range to correctly set it in the broker. The system will pickup defaults in all other cases.


## Related Commands

* [Set-BrokerServiceConfigurationData](./Set-BrokerServiceConfigurationData/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SettingName | The canonical name of the service setting that can be overridden and stored in the database. | true | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Serviceconfigurationdata
Returns the service settings set in the broker database
## Examples

### Example 1
```
Get-BrokerServiceConfigurationData
```
#### Description
Lists all the service configuration data configured by the admins in the broker
