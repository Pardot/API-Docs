# Release Notes

This page contains the release notes for the Pardot API and related documentation.

## September 2018
* added the ability to create and update a custom redirect
* added a new read endpoint for file
* added a new response parameter 'crm_fid' to Campaign.
* added a new response parameter 'salesforce_fid' to Form, Custom Redirect, and Email.

## February 2018
* fixed a few typos in the docs
* added information regarding campaign alignment

## October 2017
* added more codes to the list of [error codes](/kb/error-codes-messages/)

## August 2017

### Prospects
* Prospect assignment via `crm_owner_fid` is now available on the `create`/`update`/`upsert`/`batchCreate`/`batchUpdate`/`batchUpsert` endpoints in both v3 and v4 of the API.
* updated sections to detail how a prospect can be assigned to a user on creation passing in a `user_id`.

## July 2017

### Email
* updated "Reading Emails" section to correctly label the required param `email_id` instead of `email`.
* updated "Reading Emails" section to correctly label the required param `list_email_id` instead of `email`.

### Prospects
* batchCreate/batchUpdate/batchUpsert endpoints now return an attributes node for JSON responses that lets the client know if the request was successful or not.

## May 2017

### Prospects
* fixed various broken links in the documentation.
* fixed bug where the error array in the version 4 batch endpoints response was not correctly indexed.
* added information explaining the error response when using batch actions in v4.

## April 2017

### Prospects

`read` end-point (v4):

* This update will bring the v4 read end point into sync with the v3 end point. Archived prospects previously included in `read` responses will now be excluded when `email` is used to identify the target prospect.

## March 2017

### Visitor Activities 

`query` end-point (v3-4):

* any email activity that is related to an email list will now include the list_email_id
* any email activity that is related to an email generated from an email template will include the email_template_id
* [filter visitor activities by various object types](api-version-4/visitor-activities/#supported-search-criteria):
	* custom_url_only
	* email_only
	* file_only
	* form_only
	* form_handler_only
	* landing_page_only

#### Email

* when using the `read` end-point, you can exclude the email text and HTML body message from the response by setting [include_message](api-version-4/emails/#supported-parameters) to false.


#### Prospect
* `prospect_account_id` field is now returned by default on `query` API calls. This includes calls made with the `output`=`bulk` parameter.
#### Other

Mentions of default value: `id` for the `sort_by` query parameter have been removed from API documentation for clarity.
