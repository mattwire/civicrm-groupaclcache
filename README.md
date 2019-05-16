# Group ACL Cache improvements

This extension applies a number of experimental Smartgroup and ACL caching improvements to CiviCRM.

The extension is licensed under [AGPL-3.0](LICENSE.txt).

## Requirements

* PHP v7.0+
* CiviCRM 5.13.4

**As this extension overrides a number of core files it MUST be evaluated each time a CiviCRM upgrade is performed!**

**FAILURE TO DO SO WILL CAUSE ISSUES**

## Installation

This extension should only be installed following evaluation by a CiviCRM developer.

## Usage

Install and enable.  To disable the customisations disable this extension.

## Changes

* Partially rewrite group and acl contact caching via CRM/Contact/BAO/GroupContact.php, CRM/Contact/BAO/GroupContactCache.php, CRM/Contact/BAO/Contact/Permission.php to reduce mysql deadlocks.
* Add a lock to CRM_Contact_BAO_Contact_Permission when rebuilding cache for a single contact ID.
* Don't clear group contact cache dates until we've rebuilt it - that should stop the scheduled cache rebuild from trying to rebuild it at the same time.  

For some background see: https://issues.civicrm.org/jira/browse/CRM-18120

### Related PRs:
  * dev/core#748 Refactor of groupcontact and ACL cache https://github.com/civicrm/civicrm-core/pull/13707 and https://github.com/mattwire/civicrm-core/tree/refactor_groupaclcache
  
## Upgrading

Update all core files and re-apply master...mattwire:refactor_groupaclcache.diff