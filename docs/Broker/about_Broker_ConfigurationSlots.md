
# about\_Broker\_ConfigurationSlots

## Topic
Citrix Broker SDK - Configuration Slots and Machine Configurations


## Short Description
Overview of assigning a collection of related settings to a desktop group.


## Long Description
Collections of related settings may be applied to individual desktop groups through the creation of configuration slots and machine configurations.

A configuration slot defines a collection of related settings that are to be associated with that slot. Each machine configuration is associated with a single configuration slot and provides specific values for settings of that slot.

The SettingsGroup property of the configuration slot determines the particular collection of related settings that are associated with that slot. These groups are defined by Citrix and are not modifiable by administrators. For example, there is a particular group of Profile management specific settings that may be associated with a configuration slot. Because of the close association between a configuration slot and its collection of related settings, the full set of configuration slots is created during the site creation.

Each machine configuration is associated with a single configuration slot. The machine configuration contains policy data that provides specific values for the settings associated with that configuration slot.

Every value set in a machine configuration's policy must belong to the configuration slot's settings group. Therefore the appropriate SDK snap-in must be used to create the policy data. For example, the Profile management snap-in must be used to create the policy data for a machine configuration associated with the Profile management configuration slot.

To have particular policy settings applied to the machines in a desktop group, a machine configuration is associated with that desktop group. A machine configuration may be associated with multiple desktop groups. A desktop group may be associated with multiple machine configurations.

When a machine configuration is associated with a desktop group, the configuration inherits the delegated administration restrictions of the desktop group. Thus, if a machine configuration is associated with multiple desktop groups, an administrator can only modify the policy data of the configuration if the administrator has permission to modify every one of those desktop groups.

For detailed information about defining and assigning machine configurations, see: help New-BrokerMachineConfiguration help Add-BrokerMachineConfiguration


## See Also

* [New-BrokerConfigurationSlot](./New-BrokerConfigurationSlot/)
* [New-BrokerMachineConfiguration](./New-BrokerMachineConfiguration/)
* [Add-BrokerMachineConfiguration](./Add-BrokerMachineConfiguration/)
* [Import-BrokerDesktopPolicy](./Import-BrokerDesktopPolicy/)

