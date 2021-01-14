
# about\_Broker\_AccessPolicy

## Topic
Citrix Broker SDK - Access Policy


## Short Description
Controls client-connection-based access to desktop groups.


## Long Description
The site's access policy defines rules controlling a user's access to desktop groups. Access checks are based on details of the user's connection from their user device to the site. Think of the access policy informally as a connection-based firewall.

The access policy comprises a set of rules. Each rule:


* Relates to a single desktop group.
* Contains a set of connection filters and access right controls.

Multiple rules can apply to the same desktop group.

By default, users have no access to any desktop group within a site. A user gains access to a group when their connection's details match the connection filters of one or more rules in the access policy.

The access policy also grants control rights over desktop and application sessions. For example, it can specify which protocols are allowed for a connection from a given endpoint, and whether the user can restart their machine.

To use a resource published by a site, the user must have both access to the desktop group that contains it, and an entitlement to use the resource. Entitlements are typically granted by the site entitlement and assignment policies; see about\_Broker\_Policies for more information.


## Access Policy Rules
A single access policy rule relates to a single specified desktop group and comprises a set of connection filters and access right grants as described below.

Each rule can be individually enabled or disabled. A disabled rule is ignored when the access policy is evaluated.


### Connection Filters Overview
The connection filters in an access policy rule comprise the following:


* Local/remote client (SmartAccess) filters
* Client IP address filters
* Client name filters
* User filters

All filters have an include and exclude form that can be individually enabled or disabled. For a rule to be considered when the access policy is evaluated, at least one connection include filter must be enabled. By default, all filters, both include and exclude, are disabled.

The detailed behavior of connection filters is covered later.


### Access Right Controls Overview
The access right controls in an access policy rule comprise the following:


* Allowed protocols
* Whether machine restart, or programmatic session logoff, is allowed

The detailed behavior of access right controls is covered later.


## Details Of Connection Filters
To gain access to a desktop group the user's connection must match the filter criteria of at least one access policy rule for that group.

To match a rule, a connection must match all the rule's enabled include connection filters and must not match any of the rule's enabled exclude filters. That is, entries in exclude filters take priority.

Because all rules are evaluated independently, if an exclude filter match prevents a connection gaining access to a desktop group through one rule, the connection may still gain access to the same group through a different rule.

The filters are described in pairs below, but within a single rule a match against any exclude filter prevents a connection from gaining access through that rule irrespective of which include filters within the rule were also matched.


### Smartaccess Filters
SmartAccess filters allow filtering based on whether the client is directly connected (for example over a local area network (LAN)) or through Access Gateway. For connections through Access Gateway further filtering can be performed based on the tags supplied from Access Gateway itself. The key properties of SmartAccess filters are:


* AllowedConnections (include filter: Filtered, NotViaAG, ViaAG)
This property controls the behavior of the include filter. The default value is Filtered. The possible values are as follows:

  * Filtered (default)
    The filter matches any user connection not through Access Gateway. In addition, the filter may match user connections through Access Gateway subject to the following: if the IncludedSmartAccessTags property is empty, any such connection matches. However, if the property is not empty at least one SmartAccess tag from the filter property must match a SmartAccess tag supplied with the user's connection.

  * NotViaAG
    The filter matches only user connections not through Access Gateway. The contents of the IncludedSmartAccessTags property are ignored.

  * ViaAG
    The filter matches only user connections through Access Gateway. If the IncludedSmartAccessTags property is empty, any such connection matches. However, if the property is not empty at least one SmartAccess tag from the filter property must match a SmartAccess tag supplied with the user's connection.

  * AnyViaAG
    The filter matches only user connections through Access Gateway. The contents of the IncludedSmartAccessTags property are ignored. The behaviour of AnyViaAG is therefore the same as using ViaAG with an empty IncludedSmartAccessTags property.

    The IncludedSmartAccessTags property referred to above forms part of the include filter and is used if AllowedConnections is set to Filtered or ViaAG. It comprises a simple list of Access Gateway tags that are matched against those provided in the user's connection details.

* ExcludedSmartAccessTags (exclude filter)
A simple list of Access Gateway tags that are matched against those provided in the user's connection details. If any tag in the list matches one supplied with the user's connection, the user's connection does not match the access policy rule containing the filter.
The exclude filter has no setting corresponding to the AllowedConnections property so its behavior is determined only by the ExcludedSmartAccessTags property.

SmartAccess filters are typically used to control local (through a LAN) and remote (through Access Gateway) access to a site. A common model is to define two access policy rules rules for a group, one for local access and one for remote. The remote rule might impose restrictions on the user device having appropriate antivirus software installed, and potentially exclude certain user groups who would be allowed access over the corporate LAN (see USER FILTERS below).


### Client Ip Filters
Client IP filters allow filtering based on the IP address of the user's device. The key properties of client IP filters are:


* IncludedClientIPs (include filter)
A simple list of numeric IP address ranges that are matched against the user device. The filter matches if the device address falls within any of the ranges in the list.

* ExcludedClientIPs (exclude filter)
A simple list of numeric IP address ranges that are matched against the user device. If any entry matches the device address, the user's connection does not match the access policy rule containing the filter.

An IP address range in these filters can be specified as a simple IP address or as a range using a conventional subnet mask.


### Client Name Filters
Client name filters allow filtering based on the name of the user's device. The key properties of client name filters are:


* IncludedClientNames (include filter)
A simple list of names that are matched against the user device. The filter matches if the device name matches any value in the list.

* ExcludedClientNames (exclude filter)
A simple list of device names that are matched against the user device. If any entry matches the device name, the user's connection does not match the access policy rule containing the filter.

Note: The form of the device name presented to the site depends on the site configuration. For example, by default in these filters you cannot use the form of the name presented by Web Interface.


### User Filters
User filters allow filtering based on the identity of the user. The key properties of user filters are:


* AllowedUsers (include filter: Filtered, AnyAuthenticated, Any)
This property controls the behavior of the include filter. The default value is Filtered. The possible values are as follows:

  * Filtered (default)
    The filter matches if the user's logon token contains one or more users or user groups matching those specified in the IncludedUsers property. The IncludedUsers property is a simple list of users or user groups and is used only when the AllowedUsers property is set to Filtered.

  * AnyAuthenticated
    The filter matches any authenticated Microsoft Windows user. The contents of the IncludedUsers property are ignored.

  * Any
    The filter matches any user. The contents of the IncludedUsers property are ignored. In the current implementation this value is handled in the same way as AnyAuthenticated.

* ExcludedUsers (exclude filter)
A simple list of users or user groups. If any entry matches one in the user's logon token, the user's connection does not match the access policy rule containing the filter.
The exclude filter has no setting corresponding to the AllowedUsers property so its behavior is determined only by the ExcludedUsers property.

## Details Of Access Right Controls

The access right controls of an access policy rule determine rights that the user has over any desktop or application session that they obtain from the rule's desktop group.

The rights apply only if the user's connection matches the connection filters of a rule, and only if the user also has an entitlement to a desktop or application session from the associated desktop group.

The following properties define the access rights:


* AllowedProtocols
A simple list of communication protocols over which connections can be made to resources published by the desktop group. For example, use this to restrict protocols with high bandwidth requirements to connections originating from a LAN.

* AllowRestart
For single-session power-managed machines, allows the user to restart the machine (the machine is powered off using the capabilities of its hypervisor). For multi-session machines the user's session is simply logged off.

For a given connection, if multiple rules result in access being granted to a session from a desktop group, the user's rights are the combined rights of all the rules that matched for that group. The allowed protocol lists from all the rules are combined, and the user is granted restart rights if any one rule has AllowRestart set.


## See Also

* [about\_Broker\_Policies](./about_Broker_Policies/)
* [about\_Broker\_AssignmentPolicy](./about_Broker_AssignmentPolicy/)
* [about\_Broker\_EntitlementPolicy](./about_Broker_EntitlementPolicy/)
* [New-BrokerAccessPolicyRule](./New-BrokerAccessPolicyRule/)
* [Get-BrokerAccessPolicyRule](./Get-BrokerAccessPolicyRule/)
* [Set-BrokerAccessPolicyRule](./Set-BrokerAccessPolicyRule/)
* [Rename-BrokerAccessPolicyRule](./Rename-BrokerAccessPolicyRule/)
* [Remove-BrokerAccessPolicyRule](./Remove-BrokerAccessPolicyRule/)
* [New-BrokerAssignmentPolicyRule](./New-BrokerAssignmentPolicyRule/)
* [New-BrokerEntitlementPolicyRule](./New-BrokerEntitlementPolicyRule/)
* [New-BrokerAppAssignmentPolicyRule](./New-BrokerAppAssignmentPolicyRule/)
* [New-BrokerAppEntitlementPolicyRule](./New-BrokerAppEntitlementPolicyRule/)
* [Add-BrokerUser](./Add-BrokerUser/)

