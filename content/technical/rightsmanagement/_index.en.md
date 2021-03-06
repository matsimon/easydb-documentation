---
title: "114 - Rights management"
menu:
  main:
    name: "Rights management"
    identifier: "technical/rightsmanagement"
    parent: "technical"
---
# Rights management

## Rights

Access to resources in Easydb is controlled by rights. A right is something like `read`, `write`, `delete`.

Rights may have one or more parameters, and these can be optional or mandatory. [/api/right](/en/technical/api/right) returns the information
about right parameters. See [right](/en/technical/types/right) for a description of the parameters.
An example of a right with a parameter is `download`. The parameter would specify the version of the asset which might be available for download.

Some of the rights imply others. E.g. if a user has the `write` right for an object, s/he automatically has the `read` right.

## Access Control Lists (ACL)

Except in the case of system rights, rights management works through access control lists (ACL). An ACL consists of [acl entries](/en/technical/types/acl_entry).
Each entry assigns some rights to a group or user. Rights are additive in a way if a user gains a certain right by any of the above levels, the right cannot be withdrawn by any other level.
Rights using parameters may define there own policies on how parameters are overwritten. In our example with `download`, the best allowed download version will supersede all other versions.

An ACL entry is valid if:

- it is active
- it is in the timeframe specified by its `when` attribute, if set

Please refer to the [acl entry](/en/technical/types/acl_entry) documentation for more details.
If an ACL entry is not valid, no right is assigned.

## Realms

Rights are categorized as existing in one or more realms. [/api/right](/en/technical/api/right) returns the rights grouped by realm. System rights are contained in the realm "system".
The other kinds of rights can be attached to different types of objects, depending on the realm. The complete list of realms is:

* system: users and groups (the "system rights" part)
* objecttype-without-pool: objecttypes that do not have a pool link
* tag: tags
* pool: pools
* collection: collections
* object: user objects (only available for objecttypes with rights management)
* user: users (the ACL part)
* group: groups (the ACL part)

The rights are provided as part of the object's ACL ("_acl"), except for system rights, which are set through the "_system_rights".

## Types of rights

Easydb has the following types of rights:

- Rights for [objects](/en/technical/rightsmanagement/objects)
- Rights for [assets](/en/technical/rightsmanagement/assets)
- Rights for [pools and collections](/en/technical/rightsmanagement/poolcol)
- Rights for [users and groups](/en/technical/rightsmanagement/usergroup)
- [System rights](/en/technical/rightsmanagement/system)

