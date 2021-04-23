
# Set-Brokerrebootschedulev2metadata
Creates/Updates metadata key-value pairs for RebootScheduleV2
## Syntax
```
Set-BrokerRebootScheduleV2Metadata [-RebootScheduleV2Id] <Int32> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerRebootScheduleV2Metadata [-RebootScheduleV2Id] <Int32> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerRebootScheduleV2Metadata [-RebootScheduleV2Id] <Int32> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerRebootScheduleV2Metadata [-InputObject] <RebootScheduleV2[]> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerRebootScheduleV2Metadata [-InputObject] <RebootScheduleV2[]> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerRebootScheduleV2Metadata [-RebootScheduleV2Name] <String> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerRebootScheduleV2Metadata [-RebootScheduleV2Name] <String> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerRebootScheduleV2Metadata cmdlet creates/updates metadata key-value pairs for RebootScheduleV2. The RebootScheduleV2 can be specified by InputObject or piping.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| RebootScheduleV2Id | Specifies the RebootScheduleV2 object whose Metadata is to be created/updated by ID. | true | true (ByValue) |  |
| InputObject | Specifies the RebootScheduleV2 objects whose Metadata is to be created/updated. | true | true (ByValue) |  |
| RebootScheduleV2Name | Specifies the RebootScheduleV2 object whose Metadata is to be created/updated by name. | true | true (ByValue, ByPropertyName) |  |
| Name | Specifies the name of the Metadata member to be created/updated | true | true (ByPropertyName) |  |
| Value | Specifies the value of the Metadata member to be created/updated | true | true (ByPropertyName) |  |
| Map | Specifies a hashtable containing name/value pairs to be used to create or update Metadata members | true | true (ByValue) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Brokerrebootschedulev2
You can pipe the RebootScheduleV2 to hold the new or updated metadata.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Brokerrebootschedulev2
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.BrokerRebootScheduleV2 object.
## Examples

### Example 1
```
C:\PS> Set-BrokerRebootScheduleV2Metadata -InputObject $obj-Uid -Name "MyMetadataName" -Value "1234"
```
#### Description
This command creates/updates the Metadata "MyMetadataName" key-value pair for the RebootScheduleV2 whose instance is pointed by \$obj-Uid
### Example 2
```
C:\PS> Get-BrokerRebootScheduleV2 | Set-BrokerRebootScheduleV2Metadata -Name "MyMetadataName" -Value "1234"
```
#### Description
This command creates/updates metadata key "MyMetadataName" with the value "1234" for all the RebootScheduleV2 in the site
### Example 3
```
C:\PS> @{ 'name1' = 'value1'; 'name2' = 'value2' } | Set-BrokerRebootScheduleV2Metadata 'objname'
```
#### Description
This command creates/updates two metadata keys "name1" and "name2" with the values "value1" and "value2" respectively for the RebootScheduleV2 in the site whose name is 'objname'
