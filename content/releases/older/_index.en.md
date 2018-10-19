---
menu:
  main:
    name: "Older Releases"
    identifier: "older-releases"
    parent: "releases"

---
# Releases until 5.37

## Version 5.37.0

*Published on 11|07|2018*

### Webfrontend

*New*

* New message type for self registration form, with this it is easier to comply with the new EU privacy regulations.
* Connector: New Plugin to connect easydbs. The plugin is included as a first alpha version. It can be enabled in the base configuration and by system right.
* Support for migrated easydb 4 objects: objects in collections and presentations using the notation ```<id>@easydb4``` are recognized and visually marked. Such objects can be searched from the context menu using the Connector.

*Improved*

* Support for saving unknown (not loaded) Custom Data Types. The frontend sends the received data back to the server unchanged. Before, saving such data would result in data loss.
* Improved statistic for the export and download modal dialog. Download is now limited to 1000 objects, export is not limited.
* Filepicker for Typo3 and Drupal now sends all available IDs for the objects and files of easydb. This feature is not yet supported by the CMS plugins.
* Searchfilter now supports nested tables correctly.
* ALT/CTRL can be used in lists with checkboxes and forms with checkboxes. With that, rightsmanagement forms can be configured faster.

*Fixed*

* Bugfix for Internet Explorer 11 using a download with messages.
* In Presentations objects with no files can be used with drag & drop.


### Server

*Improved*

* Sped up searches with many pools.
* Reverse linked objects can, if unchanged, saved faster. This fixes a bug which was caused by changed JSON format of custom data types.
* Improved error messages for user email and right presets.
* CSV Export for /api/event exports a maximum of 100 characters and has corrected escaping.

*Fixed*

* Hierachical objects are index with all their ancestors not just the immediate one.
* Fixed a bug when checking password length.

### Patch-Release 5.37.1

*Published on 18.07.2018*

### Server

* Fix für empty regular expressions in password requirement check. This could lead to a wrong check in some cases.


## Version 5.36.0

*Published on 20|06|2018*

> *NOTE: This update requires a re-indexing of the index, which takes some time. Please consider this when planning your update*

### Webfrontend

*New*

* Mask Editor: Added new context menu which helps to navigate the position of fields.
* Groups: New [tab in group manager](/en/webfrontend/rightsmanagement/groups), which displays an overview of all users who are members of the selected group.
* [Script Runner](/en/webfrontend/datamanagement/search/find/script_runner): Script can be saved in the browser. Abort button added.

*Improved:*

* Presentations: If records used in presentations contain multiple images, a bar is provided to select the desired image.
* CSV Importer: Added checkbox to display either the internal database name or the frontend translation in the field selection for mappings.
* Search: Autocomplete and input for simple search and expert search improved.
* Export Manager: new checkbox to activate all database languages for export. By default, only all active frontend languages are exported.
* Detail View, Editor, New Records: The mask selection is sorted alphabetically.
* Pool/Object Type Selection in Search: Performance improved if there are many pools.
* Custom data types: Display of custom data types in the gallery, text and table view, if it is supported by the Custom Data Type.

*Fixed*

* CSV Importer: The "Reload" button no longer resets the mapping settings.
* CSV Importer: Import of linked records fixed if the records have " " in the name.
* Collections: It is now possible to upload files in collections for object types, which are not activated for pool management.
* Data model server: Fixed a bug for some special cases when synchronizing the data models.
* Editor: Entries already made are no longer discarded, when switching between sidebar editor and fullscreen editor during editing.
* New records: Fields set to "read only" are not displayed in the new editor.
* Filter: Display for centuries in date filter fixed.
* Basic configuration: Administrator E-Mail-Address is not used and has been removed from the basic configuration.

### Server

* Watermark at the pool is inherited.
* Batch processing in hotfolder.
* HTTP HEAD support for /api/objects.
* Support for all languages in CSV export.
* Fixed error generation _standard from L10N fields.
* Pool sorting also implicitly uses non-active frontend languages.
* Extension of the list of allowed file extensions.
* Disabled preview for plain text files .
* Removed administrator e-mail adress from basic configuration, because it was not used.
* Sequence of ACLs is now saved.
* Fixed XML export of decimal numbers.
* Improvements in error handling and translation.
* Container: Dependencies of containers are handled in the start script. Start order and waiting between containers is not required anymore.

### Patch-Release 5.36.1

*Published on 27|06|2018*

#### Webfrontend

* CSV Importer: Updates do not cause pool updates anymore.
* Search: Limit of 100 characters removed.


### Patch-Release 5.36.2

*Published on 29|06|2018*

#### Webfrontend

* Editor: Tags can be changed and saved without any further changes at the record.



### Patch-Release 5.36.3

*Published on 04|07|2018*

#### Webfrontend

* Editor: Fixed false "Unsaved changes" message when switching to another record in the editor.



## Patch-Release for Version 5.35

*Published on 12|06|2018*

### Server

* Fixed error in file size check before XSL transformation
* Fixed error when asset columns where used within tables/columns with long names.

---------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Version 5.35

*Published on  06|06|2018*


### Webfrontend

*New:*

* Copying records is now also possible from the context menu in the search.
* ScriptRunner: Simple scripts to download search results as CSV or JSON.
* Drupal-CMS API

*Improved:*

* Updated download format for data models. Older formats are no longer supported.
* Better interaction with the data model server (Objectstore), if set up.
* Accelerated text view.
* Improved new editor by presets for metadata and templates in fields.
* New Design in Basic Configuration.
* CSV-Importer: Support for import of images via url.
* CSV-Importer: Support for reverse nested objects.
* Group Manager: New tab showing which users belong to the group.
* User settings: Users can now see in their settings to which groups they belong.
* Minor improvements for JSON importers.
* Usability for full screen zoom improved. Zoom navigation fades away when the mouse cursor is not moved.
* Export Manager: New fields for exporting CSV.

*Fixed:*

* CTRL-Z in dynamic text areas no longer leads to a Javascript error.
* Typo3 API did not work correctly in some cases.
* Share dialog: Input field for URL enlarged
* Fixed timing problem for ad hoc collection "Worked on today" when searching in quick access.
* Fixed loading a record in the sidebar via deep link, if a message is set up on the start page.
* Detail printout revised.


### Server

> IMPORTANT NOTE: The namespace of the XML export has changed. If you use it e.g. for automatic post-editing using XSLT, you must change the old value `http://schema.programmfabrik.de/easydb-data/1.0` to the new value `https://schema.easydb.de/EASYDB/1.0/objects/`.

> IMPORTANT NOTE: Many of the included plugins are now enabled by default. If you have already activated one of these [Extension-Plugins](/en/sysadmin/installation/plugin/custom-data-type/), this will cause problems when starting the server. In this case, you can resolve it with the following options:
> * Disable the included base plugin with [plugins/enabled-](/en/sysadmin/installation/plugin/). For example, if the `extension.custom-data-type-link` plugin is used, `base.custom-data-type-link` must be disabled.
> * Deactivate the configured extension plugin. If this extension plugin is only used because it has not yet been supplied by easydb, this option is the best choice.

* Fallback in `_standard` using object ID is only output for the first data language.
* Removed `ez-standard-missing` marker class from `_standard`.
* Removed support for `elasticsearch` type in search/aggregation.
* Highlighting removed for linked objects autocompletion. It caused performance collapses in some configurations.
* Metadata import: Whitespaces at teh beginning and end of values are stripped. Empty values are not returned in mapping.
* Empty columns in CSV export are removed.
* The CSV export now provides more information for linked record.
* Fixed `_format` in `GET /api/v1/db`, when `long` has been requested.
* Namespace of XML export has been changed.
* Configuration of custom data types in plugin description has been changed, plugins may have to be fixed.
* Custom events can be defined in plugin description. The support for generic server configuration in plugin description (`yaml_config`) has been removed and raises an error on usage.
* On new installations all file types are allowed for upload by default.
* Translations for tables and column names can now be displayed in error messages.
* Handling of custom data types in CSV export improved.
* Better error handling.
* Improved speed of token autocompletion.
* Translations are loaded for correct set of languages. It removes bogus warnings.
* Schema and namespace for OAI/PMH export can be defined in base configuration.

---------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Version 5.34

*Published on  23|05|2018*


### Webfrontend

* Groups can be used to assign default settings for new users. New users, who are assigned to this group, get those user settings by default.
* Extension for date ranges in filter: filter by millennia, centuries, decades and B.C.
* New custom data type: Geo Coordinates. Allows to set own coordinates on a map.
* Toplevel folder "All folders" removed from Quick Access.
* Selection for pools/object types with SHIFT and ALT for Firefox improved.
* Extension for XML exports: Custom data types can be selected for XML exports. If the plugin supports a standard, it can be selected for the export. Otherwise, the entire data content is exported.
* It is possible to activate Custom Data Types for filters. It is also possible to hide them in the frontend, if Custom Cata Types are only meant to be accessed via API.
* Bugfix for loading the editor in the sidebar
* Bugfix for selecting & copying text in nested fields
* Bugfixes for login dialog
* Bugfix for changes in date fields via the calendar function

### Server

* Empty sub-pools are automatically deleted when deleting pools	
	 Better error handling when saving pools	
* Calls to POST /api/settings can be enabled separately (purgeall, purgedata, restart)
	 Fixed indexing of hierarchical objects	
	 Better error handling in group editor	
* Search: changelog removed from "long" format, but introduced new "full" format
* Search: more data in "long" format
	 Better error handling when deleting tags	
* Frontend info for groups in session data
* Implemented complex _standard output (e.g. from linked objects) in transition email
* Support "_standard" generated by plugins for custom types
* Fixed sorting by linked objects

---------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Version 5.33

*Published on  09|05|2018*

### Webfrontend

* When starting the application, the user frontend language is no longer automatically set if the browser has saved other settings in a cookie.
* Improvment for search: New full text type introduced. Now it's possible to search by custom tokens using single quotes.
* Improvment: If multilingualism is activated for the database, the folders are sorted alphabetically according to the active application language.
* Improvment: the minimum and maximum entries for date fields are 0 and 9999
* Bugfix for upload of JSON file for datamodel
* Bugfix for memory-leaks in detail view and editor
* Bugfix for Presets in Editor Plugin
* Bugfix for full screen and zoom in file preview for Internet Explorer 11
* Bugfix for JSON Importer
* Bugfix for collections: fixed minor usibility bugs

### Server

* ArtworkCreator and ArtworkContentDescription XMP-iptcExt are supplied in profile to be used for metadata import
* Improved enquiry when trying to delete records with references
* API extension: GET /api/l10n/user/<version> & /api/mask/<version>
* Implementet duration of access to shared collection in email template
* Increased tolerance for email address validation in base config
* multiple search tokens in /api/suggest are now combined with AND
* _relative_filename in export now relative to XML/CSV file
* Users with root rights are now allowed to add arbitrary ACLs to collections
* Limit for _objects (1000) in /api/collection
* Fixed error handling when deleting tags
* "login" won't be cleared anymore when user is archived, adjusted constraints
* Collections of archived users are deleted

---------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Version 5.32

*Published on 26|04|2018*

> *NOTE: This update requires a re-indexing of the index, which takes some time. Please consider this when planning your update*


### Webfrontend

* New: [Category Browser](/en/webfrontend/datamanagement/search/quickaccess/category) - Displays hierarchies and lists within quick access
* Improvment: Detail/Editor - separators and blocks for linked objects are renderd in "text" mode
* Improved display of separators and blocks in linked objects
* Bugfix: Object ID can also be displayed for reverse nested in detail and editor via mask settings
* Bugfix for BC dates in date fields
* Bugfix for the display of collections with rights restrictions
* Bugfix for uploads in nested fields. Update does not create a new row anymore.
* Bugfix for the search and the display of records, if the data language differs from the user language settings
* Improvment: Upload of directories is now also supported for Internet Explorer 11 and Edge
* Improvment: The mask selection is now also shown in the editor popover
* Improvment: The user manager now also supports the search by user ID
* Improvment: Search filters can now be saved as preferences and are displayed by default for new calls
* Bugfixes for [Editor-Plugin](/en/webfrontend/administration/base-config/editor)
* Bugfix for Export Manager
* Bugfix: Displaying mandatory fields within panels has been fixed
* Bugfix: The alphabetical sorting of collections now corresponds to the preferred data language of the user

### Server

* Size of XML files is checked before XSL transformation, defaults to max 10 MB
* Improved error message for duplicate export names
* Asset link sync to EAS is enabled by default now. Assets, which are not linked in easydb are automatically removed from the EAS.
* show_in_collections in /api/v1/objecttype for [Category Browser](/en/webfrontend/datamanagement/search/quickaccess/category)
* Bugfix for fix for wrong owner in change history
* link"/"unlink"/"create_in_collection" rights on collections are inherited now
* New export profile: Metadata can optionally be replaced or obtained
* Bugfix for login error using previously deleted user account
* Search language for pool aggregations fixed (requires frontend language)
* _standard is returned for all enabled languages
* Fixed indexing of reverse-nested EAS fields
* /api/v1/settings now returns current schema version

---------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Version 5.31

*Published on 12|04|2018*

*NOTE: This update requires a re-indexing of the index, which takes some time. Please consider this when planning your update*

### Webfrontend

* Improvements and bugfixes for JSON Importer
* Improvement in pool selection: If a non-active pool contains an active subordinate pool, the superordinated pool is marked with a minus.
* Improvement for hierarchical object types: Hierarchies now behave accordingly in table view as in standard and text view
* Improvement for multilingual output: The detail view now shows all languages (not only the preferred language) when entries exist
* New option for masks in the data model: It is now possible to hide the labels for fields in nested groups
* Extension for messages: new option [Permanent message in user menu](/en/webfrontend/administration/messages) added. Note appears as a button next to the user settings in the header.
* Sorting for search results now also applies to custom data types (from plugins)
* Pool management: Refinement of rights management by assigning an [owner](/en/webfrontend/rightsmanagement/pools)
* Data model: [JSON Download/Upload](/en/webfrontend/administration/datamodel) for schema, masks and localization
* Display of object ID via mask settings in detail for editor
* CTRL-right-click now opens the browser menu
* CTRL-ALT-Click activates the selected checkbox and all subsequent checkboxes (not those in front of it) (e.g. Data Model > Masks or Basic Configuration File Types for Upload)
* User management: Group names are also exported to CSV
* User management: Excel UTF-8 compatibility for CSV
* User management: Improved loading time
* Bugfix: several fixes for problems with fast clicks
* Bugfix: for multilingualism input fields: For entries in hidden languages, the input field of the languages that are not used are no longer marked as mandatory fields.
* Bugfix: Editor did not load if an incorrect web link was loaded into a data field via API
* Bugfix for collections: rights check for "create in collection" fixed
* Bugfix for collections: *Select all* fixed
* Bugfix for login: Link and link text to start a login via SSO now appears in login and is set via base configuration
* Bugfix: Number of objects in list was not updating correctly after new records were added or deleted.
* Bugfix for messages: Message for start page in search was not displayed correctly
* Bugfix for pool management: Switching between pools caused wrong error message
* Other minor bugfixes

### Server

* Removing files in base configuration (e.g. logo) is allowed
* Empty localizations are skipped in API output for base types
* Object id as option in mask definition
* Translated column names in CSV export
* Collection reference field is updated on user changes
* Reintroduced owner rights for pools
* Improved speed of /api/eas/rput
* Only configured database languages are included in index. Adding new languages requires a reindex, which is not enforced on configuration changes. Activating a new schema version is required to rebuild the index.
* Fixed link in workflow e-mail
* Fixed indexing error related to complex masks
* Reindex collection if one of the parent collection changed
* Fixed generate_rights in collection search

---------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Version 5.30

*Published on 14|03|2018*

### Webfrontend

* Improvements for JSON Importer
* First version for sorting of custom-data-types available
* New code documentation: Alphabetical index of used classes in easydb5. Is currently still under construction > [Preview](https://programmfabrik.github.io/easydb-code-documentation)
* New github repository for easydb plugin examples > [easydb-plugin-examples](https://github.com/programmfabrik/easydb-plugin-examples)

### Server

* Bugfix: Fixed full text search for backward-linked hierarchical object types
* Bugfix: Error in CSV export fixed
* Bugfix: Fix for lookup feature in POST /api/db
* Pool rights now affect subordinate pools
* Fixed output of asset information in multiple fields, so that search for asset attributes from multiple fields is now possible
* Added /api/eas/rput request to speed up migration. This API is still under construction (changes reserved).
* New data language "und" (="undefinite") for non-identifiable languages added
* Mapping is updated when "pool management" is activated for an object type
* API: Collection API extended to specify contained objects when saving a folder
* API: API now tolerates null bytes in JSON inputs

## Version 5.29

*Published on 28|02|2018*

### Webfrontend

* Saving and loading the basic configuration setting to and from a file.
* The "Detect versions" setting in the file uploader is saved for users.
* Support for sorting linked records within repeating groups.
* Bugfix: Some language settings in the browser caused a load loop when logging in, if easydb was configured with messages.
* Bugfix: Autocompletion was partially overlapping in the Internet Explorer.

### Server

* API: Added filter for user_ID
* API: Limit & Offset implemented as URL parameter for collection/list-API
* API: Collection/list API is limited to 1000 records
* Minor bugfixes

## Version 5.28

*Published on 14|02|2018*

*NOTE: This update requires a re-indexing of the index, which takes some time. Please note this if you plan to update*

### Webfrontend

* Improved block rendering: The juxtaposition of fields for blocks, is now also possible for panels and tabs and for complex multiple fields.
* Data model: Download and upload of data models as CSV (only for object types).
* Data model: Improved support for Objectstore for distributed data model development.
* Server Manager (Plugin): New menu to restart the server, to delete all data and to delete the data model.
* Bugfix for Google Chrome: Testlink for share URL started a new user session.
* Bugfix: CSS developer did not open.
* Bugfix: Language selection in collection setting now diplays the correct language list.
* Bugfix: "Select all" for Collection works correctly again.
* Improvement: Autocompletion in the search field improved, when entries are typed fast.

### Server
* Removed locking in /api/user to improve performance
* USER_LOGIN event for LDAP/SSO authentication
* Added "IPTC:Caption-Abstract" as "description" source in metadata import
* API to reset database and user-defined schema
* Fixed error in handling of namespaces in XSLT
* Added "latin" as a new data language ("la")


## Version 5.27

*Published on 31|01|2018*

#### Webfrontend

* Block rendering in masks (ordering fields side by side), whereby the width of the fields can be set to 25%, 50%, 75% or 100%.
* Bugfix for watermark versions: if an equivalent version without watermark exists, it is displayed preferentially to the user.
* Highlighting is disabled in favor of speeding up search queries for complex data models.
* Custom field selection now shows the database name and the localized field name (exporter).
* The allocation of names for collections is now multilingual.
* Bugfix for custom data type search within multiple fields.
* Bugfix for the selection dialog of object types and pools in the search.

#### Server

* Users can be found by all email addresses, which are saved for the user (not only the preferred email address).
* Fixed loading of Dublin Core mapping for OAI/PMH export.
* Display name for recipient can be set in configuration.
* Restored default type for XSLT output (XML), directives in XSL file are optional again.
* Server startup time reduced.
* Hotfolder process is less CPU hungry.
* LDAP plugin allows group lookup using multi-value attribute.
* Fixed "forgot password" link in the text part of respective emails.

## Version 5.26

*Published on 18|01|2018*

*NOTE: This update requires a re-indexing of the index, which takes some time. Please note this if you plan to update*

#### Webfrontend

* Data model (development): Several fields can be created at once for object types
* Data model (development): Object types can be copied with corresponding masks
* Data model: Sorting for object types (alphabetical and by main/sub-object type)
* Events can now be searched by ID

#### Server

* added _last_updated_date to the JSON representation of the export
* Pool rights are considered when downloading assets from repeating groups
* Email with generated password corrected
* Multiple events can be deleted with one server request
* Fields for some new languages and fonts have been added. The search is not yet matched to the individual languages.


## Version 5.25

*Published on 20|12|2017*

#### Webfrontend

* Pool info display in detail
* User agent (browser name) is saved in logs for frontend errors
* Selection of user or group is displayed with icon
* System right to switch off the column filter
* Expert search for hierarchy status of an record
* SSO login: Support for "window_open=self"
* Messages for the start page of the search
* Extended login message in login dialog
* Field attribute "ez5-field-name" in detail / editor
* Templates "supplement" works for multi-line text fields and multiple fields
* Download manager shows number of titles
* CSV hierarchy option in the exporter
* To monitor your easydb you can now use our free [plugin](https://github.com/programmfabrik/check-easydb5) which works with either Nagios or Icinga.

#### Server

* CSV and easydb XML export can be used with unlimited batch size
* easydb 4 password hashes can be migrated
* Expire date removed from email confirmation links
* BC years are now working correctly in date ranges
* Collections are reindexed if sub-collections are moved
* Groups from LDAP can be used alongside SSO authentication
* Reference and short name fields in base type now have to be unique
* User is questioned if tags should be deleted which are still in use
* Improved error messages for UNIQUE constraint violations


## Version 5.24

*Published on 06|12|2017*

#### Webfrontend

* Info about the last update of the record in detail view and editor
* Templates are provided in all editors
* Placeholder object icons (and text) can be configured via CSV.
* Settings for print quality and style.
* Copy function for rights.
* Copy function for collections.
* Improved usability of the presentations.
* Bug fixes in CSV-Importer, detail, folder search, data model editor, etc.

#### Server

* Cleanup when deleting tags
* Mapping of color depth and resolution (DPI) for images.
* Unicode normalization for the search.
* Behaviour of the `unique_id` plugin functions more adapted to PostgreSQL sequences, avoids long locking periods.
* Reference fields for base types are loaded/stored.
* Confirmation link for e-mails no longer expires.
* Bug fixes and internal improvements.

## Version 5.23

*Published on 22|11|2017*

#### Webfrontend

* Headlines for tabs in masks
* Pool-Deep-Link /pool/<shortname> added, works for all pools for which shortname is set
* Shift to expand the marking is supported
* Print text view and different qualities
* Display of old versions in detail
* Link in the tray for documentation, configurable in the basic configuration
* Records can be used as templates in the group editor
* Navigation in group editor, so the editor loads a lot faster with many objects
* Automatic comment in the group editor
* SSO: Logout can be configured
* Plugins: Custom settings for masks extended
* Bugfix: Saving of reverse nested not visible is possible again
* Bugfix: Sorting in the object type/pool selection is now localized
* Bugfix: Search file names now allows all search functions

#### Server

* Customer-specific e-mails can be provided via plug-ins (e. g. per solution).
* The group editor provides a comment for all changes.
* Tag updates trigger user object indexes.
* System rights can only be passed on, if the owner posses them.
* Collections can store remote records
* Deletion of non-confirmed e-mails (within 24h) disabled.
* Owner of reverse linked objects is preserved.
* Changelog search extended.
* Bug fixes and other minor improvements.


## Version 5.22

*Published on 08/11/2017*

#### Webfrontend

* New Mask setting for Boolean values to show the status "false" in the detail view
* New Mask setting to limit map display to certain values
* Support of D.C. data in date fields
* Extension for the export of linked records
* Search: Display of sub-records in hierarchical records
* Search: Extension allowing users to search changes (not only the last change)
* Editor: Bug fix for moving multiple fields
* SSO: Logout support for single sign-on (such as Shibboleth)

#### Server

* Old record versions now also provide old tag links
* Improved error messages and user decisions when deleting hierarchical records
* Extension for the export of linked records
* Parameters for editing ACLs/system rights for users and groups moved from permissions to system rights
* Optimized indexing of old data record versions
* Improved possibilities for searching in the changelog
* Other minor bug fixes and improvements

## Version 5.21

*Published on 25/10/2017*

#### Webfrontend

* Detail: Plugin interface for detailed view in the sidebar.
* Map: [Display of GPS coordinates](/en/webfrontend/datamanagement/search/detail) on a map (OpenStreetMap) when included in images. This plugin is [Open-Source](https://github.com/programmfabrik/easydb-detail-map-plugin)
* Custom Data Types: NULL and Unique are available in the data model
* Improved navigation in the event display
* Bug-Fix for login for anonymous users
* User Manager: Create LDAP and SSO users before they log in
* Option to change the link text for SSO logins
* Output of IDs for object types, masks and pools to simplify the use of the API

#### Server

* Asset metadata includes GPS-Information, if the file contains it.
* Path information for hierarchical objects in XML export has been enhanced.
* XML namespace for "easydb"XML export, especially for OAI/PMH interface.
* Checks in the data model ("not_empty","email","regexp","range") are no longer forced in the database.
* Memory leaks in the exporter have been removed.
* Request (HTTP 202) when deleting hierarchical objects with subordinate objects.*
* Deleting groups which are referenced in the changelog allowed.
* Other minor bug fixes and improvements.

## Version 5.20

*Published on 12/10/2017*

#### Webfrontend

* Presentations can be deleted without deleting the entire collection.
* Fixed new login for users with unfinished tasks.
* Uploader: race condition fixed for large bulk uploads when clicking too fast.
* Data model: Mask options for EAS standard fixed.
* Table view with one column fixed in some configurations.
* Window compat and jQuery CUI compat layer removed.
* Fixed Powerpoint export of presentations.
* Detail / Editor: Render improvements for small lists.
* Plugin interface for export dialog.

#### Server

* Welcome email can be sent to multiple users.
* Exports are set to "failed" if the exporter terminates unexpectedly.
* Invalid mask configuration (different nesting settings for the same field) is detected and rejected.
* Plugin API extension (access to pseudo session during export).
* Fixed error for index update after changing nesting settings.
* Adjustments in the search API.

## Version 5.19

*Published on 27/09/2017*

With this release, easydb has switched to a new version of the Elasticsearch software. The change is done automatically when updating the docker containers, but there is a setting that has to be changed on system administration level, as it is not possible to change it via updated docker images:

The value for the [sysctl](https://en.wikipedia.org/wiki/Sysctl)-key [vm.max_map_count](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html) needs to be increased:
```
sysctl -w vm.max_map_count=262144
```
This can be set in the [Start- Script for Elasticsearch-Container](/en/sysadmin/installation) or via the instruments used in the Linux distribution (`sysctl. conf`).

The update to the new Elasticsearch version also requires a re-indexing, which is why the operation of larger databases may be interrupted for several hours.

#### Webfrontend

* Modification and redesign of editor, detail, text view, table view and expert search
* Selection of masks in expert search
* Optional batch and version detection for files during manual upload
* Improved memory management
* Setting option for masks how to start panels (open/closed)
* Openning panels at the same time
* Mask option for a shortend output of multiple fields
* Improved Design for the input and output of Custom-Data-Types (e.g.  Weblink and GND)
* Using the NPM-Version of Coffeescript-UI
* "Select all" in collections

#### Server

* Porting to Elasticsearch 5
* Improved E-Mail-Handling
* Searching User typs possible
* Events of type OBJECT_INDEX and API_PROGRESS are deleted after one week.
* Status "expired" for exports
* general "bag_read"-right via "system. group"-system right possible
* Resetting of standard masks to object type specification in /api/objecttype possible
* Displaying multiple records in /api/db possible
* Improving search
* Fixed error when running /api/collection at the same time
* Update for ACLs when deleting pools
* /api/event/list accelerated
* XML export of more types possible (date ranges, fixed point numbers)

## Version 5.18

*Published on 06/09/2017*

When updating to this release, a new database index must be created. Also Elasticsearch needs an reindexing. In the case of a larger database, it is therefore likely that operations will be interrupted for several hours.

#### Webfrontend

* CSV Importer: Multiple field support for EAS columns
* Reloading Tags & workflows when saving fails
* Bugfix: Link to Collection from Detail view
* Bugfix: Esc if tooltip is active above an active layer
* Bugfix: Search for multiple words has swapped the order of words

#### Server

* Corrected and extended email templates & variables used in emails
* added Georgian language for data (ka-GE)
* Tag names for XML export
* improved error handling, e. g. when deleting tags
* Acceleration of e.g. export in case of of many events

## Version 5.17

*Published on 08/23/2017*

### Webfrontend

New objects: Improvements for the uploader for large amounts of data.
Search: The automatic search for new objects has been revised.
Support for [Vivaldi browser](https://vivaldi.com/), but test platforms are still Mozilla Firefox, Chrome + MS Edge.
Improved error management for CMS plug-ins.
Improvements in memory management.

#### Server

Deeplink: API supports versions of objects (by version number or date)
CSV Exporter: Error during export has been fixed
CSV Exporter: CSV headers have been modified
XML Exporter: Objects are exported with namespace attribute `xmlns`.
XML Exporter: Field `_standard` of linked objects is exported
XML Exporter: URLs to assets are extended by `disposition/inline` to allow display in the browser
Fixed an error when generating EAS file paths
OAI PMH: Deeplink URLs get the parameter `auth=oai_pmh` when exporting
Fixed a password reset error

## Version 5.16

*Published on 08/09/2017*

### Webfrontend

Group Manager: Display of the internal ID, Copy button.
CSV exporter: Excel compatible output for UTF-8 (BOM)
Code support for term boosting in QueryElementToken and QueryElementFulltext
Performance: Load folders faster
Performance: memory requirements of the application have been optimized
Bugfix: Lasso at zoom > 100%.
Bugfix: Displaying previews in the data model didn't work for some masks

#### Server

Byte Order Mark is output during CSV export
Time values in CSV export are exported ISO 8601 compliant
Internal handling of ISO 8601 time values has been standardized
Collection Post Processing in `api/search` has been improved
Missing entries in multilingual fields are no longer overwritten with an incorrect language
Deeplink `.... /file_version/group/<group>` has been fixed
Pool rights are sorted alphabetically


## Version 5.15

*Published 07/26/2017*

#### Webfrontend

ExportManager: Downloads can be viewed with ALT-Click
Logout now leads to the start page again and again, not to the login
CSS classes for designability of detail + editor
Support for phrase searches for users, groups, pools and folders
Improved folder loading for databases with many rights
Bugfix: When saving with invisible fields the required fields were not checked correctly
Bugfix: Selection of a father entry for newly created entries in small popover editor
Bugfix: Uploading XSLT files in the configuration is allowed, even if otherwise prohibited

#### Server

CSV export extended
CSV output of events extended
Selection of replacement version corrected during export
Versions that are not subject to rights management can now be downloaded
Metadata mapping for Typo3 plugin enabled
File upload for special files corrected
Email templates updated
Improved e-mail address validation

## Version 5.14

*Published 07/12/2017*

#### Server

Email addresses with uppercase letters are now allowed
Restructuring of the rights list
Export corrections
fixed bug when loading multiple production plugins

#### Webfrontend

Support for different colored tags
File versions: Direct name input before creating new versions
Search for "#<system-id>" in main search field
Detail / Editor: Support of alphabetically sorted multiple fields
Bugfixes in the CSV importer, metadata tool, detail, search, collections


## Version 5.13

*Published on 28.06.2017*

Changes to the search index require a re-indexing. Depending on the database size, this can result in a limitation of usability lasting several hours.

#### Server

* Search index takes fulltext setting to nested tables
* Fix for download transport without packer
* Expand the information about download transport files in the export API
* Correction of the EAS links in the export
* Preparation for hotfolder import into linked tables
* Search corrected with accents
* Enhancement to `exclude_fields` in the search API
* Optimization when generating `ALL_FIELDS` links

### Webfrontend

* Download and export of remotely linked files, which are displayed in the detail viewer
* A robots.txt ensures that search engines do not index
* Expert search: Improved tokenizer for autocompletion in text fields
* CSVImporter: Bugfixes when importing linked objects
* Other minor bug fixes

## Version 5.12

*Published on 14.06.2017*

### Webfrontend

* Support for single-field legal management
* Support for serial images, versions(RAW, Jpeg) and remote objects during upload
* Improved drag & drop in folders
* Date selection possible without time
* CSVImporter: Support for multilingual link fields in search and creation
* Troubleshoot grouping in the filter tree
* Bug fixes and performance improvements

#### Server

* All-Fields-Mask also links the mask with all fields for links
* Field filter I/O
* Update date for user changes
* Hotfolder extensions
* `OBJECT_DELETE` event for archived users
* Wildcard search corrected, case no matter now
* LDAP and SSO users now get workbooks. In order to benefit from this, the user "ldap" or "sso" stored in the easydb has to be deleted. This will be created again on the next login.
* Selection of the field to be exported for the CSV export corrected

## Version 5.11

*Published on 31.05.2017*

#### Server

* Restrict fields after mask settings(full text search) for phrases search
* New API request `settings`
* Filter for `/api/user`
* `OBJECT_INDEX` events are always generated for assets, even at low priority
* Bug fixes

## Version 5.10

*Published on 17.05.2017*

#### Webfrontend

* Hierarchy browser in detail(for hierarchical object types).
* In table view, the column widths can be adjusted manually.
* Hierarchy checkbox is removed from the object type/pool selector.
* Hierarchy checkboxes in each view as option.
* Improved marking of required fields, especially in the group and new editor.
* CSV Importer: Support for decimal fields, import of MS Access data(YYYMMDD format).
* Bug fixes and performance improvements.

#### Server

* Download of large files corrected.
* Caching policy is left to the plugins.
* Custom settings in schema/masks for more field types.
* Missing foreign key in the data model.
* Links corrected in XML export.
* Import of bidirectional data corrected with the group editor.
* Failed to create indexes with long names fixed.

## Version 5.9

*Published on 03.05.2017*

#### Webfrontend

* Schedule with presets for emails and export transport
* Support for optional separators in field identifiers.
* Printing now works in Internet Explorer.
* Mark all hits in the secondary search.
* CSVImporter: improvements and fixes.
* Plugin: Wordpress CMS Transport(Beta).
* Plugin: export transport FTP is now a plugin.
* Troubleshooting and speed optimization

#### server

* Login names and e-mail addresses must now be unique regardless of the case.
* Group assignment for LDAP and SSO authentication has only validity for the session and is no longer persistent.
* Index error during import with mask "\ _all \ _fields" fixed.
* Parallelism removed during export to increase reliability.
* Added minutes accuracy for scheduler.


## Version 5.8

*Published on 19/04/2017*

#### Webfrontend

* CSVImporter: Support for multilingual fields(hierarchy + updates)
* New system privileges to hide group and user managers, but still allow access via the API
* Improved self-registration dialog
* File download of linked objects containing the files displayed in the standard(single download only)
* "Discard Changes?" Dialog in Profile & Tag Manager
* Graphical improvements
* Troubleshooting: Language selection at restart was always "en-GB".
* Other bug fixes

#### server

* More fields in XML export
* New parameter "hide_frontend_app" for system rights "system.user" & "system.group"
* Search & Suggest in more fields
* Fixed issue collection issues
* Fixed bug when evaluating plugin configuration
* Fixed DB error in export scheduler

## Version 5.7

*Published on 05.04.2017*

#### Webfrontend

* Display of linked objects from the detail in the search.
* CSV Exporter for users
* Supports multilingualism, date and ID columns in the CSV importer
* Single-Sign-On supports authentication in a separate browser window.
* Bug fixes

#### server

* User-blocking in case of multiple attempts at client blocking
* Support for custom types in the search
* Max. Length for ngram search is increased from 30 to 50
* Suggestion for file properties corrected
* Archived users are not output via the API
* XML namespace corrected in export metadata mapping
* No persistent DB connection in the Janitor more
* Thread leak in the Exporter fixed
* Fixed errors when saving e-mail addresses

## Version 5.6

*Published on 20.03.2017*

#### Webfrontend

* Connection of [cloudsight.ai](http://cloudsight.ai).
* Improved language selection at the first start of easydb.
* Bug fixes & performance enhancements

#### server

* Output of old record versions accelerated
* Object URLs in XML export
* Indexing of bidirectional links improved
* Handling of tags in the group editor corrected without other changes
* Output of standard EAS block unified for records without assets

## Version 5.5

*Published on 08.03.2017*

#### Webfrontend

* CSV importer for users and lists
* Performance improvements & bug fixes
* Support for custom colors in basic configuration.
* A Markdown link opens in a separate browser window.
* Fix for keeping the visible order when reordering in collections.

#### server

* New event `USER_CREATED`
* LDAP support
* Additional columns for bidirectional links are copied
* Removes tag filters from object types
* Fixed bug in collections operations
* Fixed metadata with NULL bytes
* Improved speed for collection requests

## Version 5.4

*Published on 22.02.2017*

#### Webfrontend

* Change to new design
* Performance improvements & bug fixes

#### server

New:

* ZIP64 support for exports.
* Timeout of users(for example, if there are too many attempts to log on when logging in).
* System name visible without login.
* Root right no longer visible to non-root users.
* Event for base config update.
* UNIQUE Contraints for date ranges.
* Plugins can create their own events.

Added:

* Deeplink extensions.
* "AOContentDescription" for export profile.
* Better error messages and translations("L10N").

Repaired:

* Export the complete search.
* Remove all ACLs.
* The password-forgotten link.
* Setting "inactive" to ACLs.
* More details and little things. For more information please ask specific questions at support@programmfabrik.de.
* Speed ​​of ACL treatment improved.


## Version 5.3

*Published on 31.01.2017*

#### server

* Custom Datatypes: more comprehensive support for search and aggregations. Caution: this change requires an adjustment of the configuration of the Custom Datatype plug-ins.
* Search:/api/search works only with "aggregations", "facets" are no longer supported.

## Version 5.2

*Published on 02.12.2016*

#### Webfrontend

* Conversion of folders, search and finder.
* Redefined selection paradigms.
* Directly accessible flyout buttons as addition to the Context menu.

#### server

* OAI/PMH interface.
* Deep link interface.
* Extension for Custom Data Types.

## Version 5.1.1

*Published on 10.11.2016*

Bugfix # 39365: - dbapi_import: fix UPDATE: insert dirty job for deleted reverse nested objects

## Version 5.1

*Published on 06.11.2016*
