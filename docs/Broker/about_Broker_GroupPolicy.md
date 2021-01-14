
# about\_Broker\_GroupPolicy

## Topic
Citrix Broker SDK - Group Policy for VDA Configurations


## Short Description
Overview of Citrix Group Policy settings that control VDA behaviors.


## Long Description
A VDA configuration policy is a collection of settings that specify how a VDA should initialize its environment when a user logs on. Settings that are to be enforced when a specific user session is created are user settings. Settings that are always applied to all user sessions are computer settings.

Multiple policies contianing multiple settings can be defined. Filters can be specified in a policy to define how the settings included in the policy are to be applied, based on data such as the user name, the name of the client, from which the user session is originated.

There is a policy processing engine (CSE) running on each VDA. The engine is responsible for processing the policies downloaded to the VDA from the site, to which the VDA is registered, and/or the domain the VDA is in. The engine uses policies from all the sources to calculate a net result, which is a single set of unique settings that can be used by the VDA to initialize the environment when a user logs on.

A policy object contains a set of properties that describe the object. It also contains a set of settings, which are specific VDA configuration settings, as well as a set of filters, which specify how the settings in the policy are applied.


* A setting is a single piece of data that specifies a certain behavior for a user session. For example, a wallpaper setting is used to control if a wallpaper should be displayed when a user logs on.
* A filter is a statement that specifies how the settings in the policy are to be applied. When evaluted with the input data required by the filter, the statement yields a Boolean value. A true result tells the policy engine that the settings should be applied. A false result tells the policy engine to not apply the settings.

To define a VDA configuration policy, specify a name for the policy and a priority that indicates a precendence for the settings in the policy when the policy is evaluated togehter with other policies by the Citrix policy engine (CSE) running on a VDA. A name and an optional brief description can be specified to help identifying the policy and its purpose.

Four database tables are defined to store policy data. They are blobs, policies, settings, and filters.

A blob is a container of a collection of policies. For each site, there is always a default blob defined and this blob contains all the site policies.

A policy is a collection of settings and filters.

A setting specifies a configuration that will be honored and enforced by a VDA component.

A filter is a predicate that specifies the condition for the settings in the policy to be applied or not applied.

There can be multiple policies in a blob. There can be multiple settings in a policy. There can be multiple filters in a policy. A setting can be used in multiple policies but can only be used once is a policy. Multiple filters can be specified in a policy and the final result of combining all the filters decides if the policy should be applied or not.

For detailed information about defining policy objects, see: help New-BrokerGpoBlob help New-BrokerGpoPolicy help New-BrokerGpoSetting help New-BrokerGpoFilter


## See Also

* [New-BrokerGpoBlob](./New-BrokerGpoBlob/)
* [New-BrokerGpoPolicy](./New-BrokerGpoPolicy/)
* [New-BrokerGpoSetting](./New-BrokerGpoSetting/)
* [New-BrokerGpoFilter](./New-BrokerGpoFilter/)
* [Get-BrokerGpoBlob](./Get-BrokerGpoBlob/)
* [Get-BrokerGpoPolicy](./Get-BrokerGpoPolicy/)
* [Get-BrokerGpoSetting](./Get-BrokerGpoSetting/)
* [Get-BrokerGpoFilter](./Get-BrokerGpoFilter/)
* [Set-BrokerGpoPolicy](./Set-BrokerGpoPolicy/)
* [Set-BrokerGpoSetting](./Set-BrokerGpoSetting/)
* [Set-BrokerGpoFilter](./Set-BrokerGpoFilter/)
* [Remove-BrokerGpoBlob](./Remove-BrokerGpoBlob/)
* [Remove-BrokerGpoPolicy](./Remove-BrokerGpoPolicy/)
* [Remove-BrokerGpoSetting](./Remove-BrokerGpoSetting/)
* [Remove-BrokerGpoFilter](./Remove-BrokerGpoFilter/)

