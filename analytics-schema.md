Airkit collects data on the behavior of your applications. This includes information on what Events are triggered, how long users interact with your application before completing their Journeys, and how many users begin a Journey at all. In addition to collecting general information, Airkit will also log any Custom Events that have been defined in an application. 


Collected data is stored in Airkit’s internal database, from which data can be read into various analytics platforms via the tool Jetset. This data is structured into various tables, each of which contain their own set of properties. 


## Adapter

Data pertaining to external integrations and how they are authenticated. 
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "h-2": "",
    "0-0": "ORGANIZATION_ID",
    "0-1": "VARCHAR",
    "0-2": "",
    "1-0": "ADAPTER_ID",
    "2-0": "CREDENTIAL_TYPE",
    "3-0": "ADAPTER_KEY",
    "4-0": "DISPLAY_NAME",
    "5-0": "DESCRIPTION",
    "6-0": "CREATED_YEAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "VARCHAR",
    "5-1": "VARCHAR",
    "6-1": "NUMBER",
    "7-0": "CREATED_MONTH",
    "8-0": "CREATED_DATE",
    "7-1": "DATE",
    "8-1": "DATE",
    "9-0": "CREATED_TIME",
    "10-0": "MODIFIED_TIME",
    "9-1": "TIMESTAMPNTZ",
    "10-1": "TIMESTAMPNTZ",
    "11-0": "AUTH_PARAM_TYPE",
    "12-0": "AUTH_PARAM_NAME",
    "13-0": "ACCESS_TOKEN_VERB",
    "14-0": "AUTH_GRANT_TYPE",
    "15-0": "CAPABILITIES",
    "15-1": "OBJECT",
    "11-1": "VARCHAR",
    "12-1": "VARCHAR",
    "13-1": "VARCHAR",
    "14-1": "VARCHAR"
  },
  "cols": 2,
  "rows": 16
}
[/block]
## App

Basic data regarding each application.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "APP_ID",
    "2-0": "DISPLAY_NAME",
    "3-0": "DESCRIPTION",
    "4-0": "CREATED_YEAR",
    "5-0": "CREATED_MONTH",
    "6-0": "CREATED_DATE",
    "7-0": "CREATED_TIME",
    "8-0": "MODIFIED_TIME",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "NUMBER",
    "5-1": "DATE",
    "6-1": "DATE",
    "7-1": "TIMESTAMPNTZ",
    "8-1": "TIMESTAMPNTZ",
    "h-2": "Description",
    "0-2": "Unique identifier of the [Organization](doc:airkit-organizations) the app was built in.",
    "1-2": "Unique identifier of the application.",
    "2-2": "Application name, as defined when examining the app in the [Console](doc:console).",
    "3-2": "Application description, as defined when examining the app in the [Console](doc:console).",
    "4-2": "Year the application was created.",
    "5-2": "Month the application was created.",
    "6-2": "Date the application was created.",
    "7-2": "Time the application was created.",
    "8-2": "Time the application was last modified."
  },
  "cols": 3,
  "rows": 9
}
[/block]
## App Subscription

Data pertaining to packets of information passed to external sources via Web Hooks. 
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "APP_SUBSCRIPTION_ID",
    "2-0": "DISPLAY_NAME",
    "3-0": "CREATED_YEAR",
    "4-0": "CREATED_MONTH",
    "5-0": "CREATED_DATE",
    "6-0": "CREATED_TIME",
    "7-0": "MODIFIED_TIME",
    "8-0": "DEPLOYMENT_ID",
    "9-0": "DATA_SOURCE_ID",
    "10-0": "EVENT_SOURCE_ID",
    "11-0": "WEBHOOK_CATEGORY_KEY",
    "12-0": "WEBHOOK_IDENTIFIER",
    "13-0": "WEBHOOK_EVENT_SOURCE",
    "14-0": "PROPERTIES",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "NUMBER",
    "4-1": "DATE",
    "5-1": "DATE",
    "8-1": "VARCHAR",
    "9-1": "VARCHAR",
    "13-1": "OBJECT",
    "10-1": "VARCHAR",
    "11-1": "VARCHAR",
    "12-1": "VARCHAR",
    "14-1": "OBJECT",
    "6-1": "TIMESTAMPNTZ",
    "7-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 15
}
[/block]
## Asset

Data on Assets used in or downloaded by applications.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "ASSET_ID",
    "2-0": "ASSET_KEY",
    "3-0": "ASSET_VERSION",
    "4-0": "DISPLAY_NAME",
    "5-0": "CONTENT_TYPE",
    "6-0": "CONTENT_SIZE",
    "7-0": "EXPIRATION_TIME_HOURS",
    "8-0": "EXPIRATION_TIME_MINUTES",
    "9-0": "EXPIRATION_TIME_SECONDS",
    "10-0": "EXPIRATION_TIME_MILLIS",
    "11-0": "VISIBILITY",
    "12-0": "STATE",
    "13-0": "SCOPE",
    "14-0": "REGION",
    "15-0": "CREATED_YEAR",
    "16-0": "CREATED_MONTH",
    "17-0": "CREATED_DATE",
    "18-0": "CREATED_TIME",
    "19-0": "MODIFIED_TIME",
    "20-0": "VALIDATION_ERRORS",
    "21-0": "EXTRA_INFO",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "NUMBER",
    "4-1": "VARCHAR",
    "5-1": "VARCHAR",
    "6-1": "NUMBER",
    "7-1": "NUMBER",
    "8-1": "NUMBER",
    "9-1": "NUMBER",
    "10-1": "NUMBER",
    "11-1": "VARCHAR",
    "12-1": "VARCHAR",
    "13-1": "VARCHAR",
    "14-1": "VARCHAR",
    "15-1": "NUMBER",
    "16-1": "DATE",
    "17-1": "DATE",
    "20-1": "VARCHAR",
    "21-1": "OBJECT",
    "18-1": "TIMESTAMPNTZ",
    "19-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 22
}
[/block]
## Audit Event

Data pertaining to the details of Audit Events, which are used for things like compliance tracking.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "EVENT_ID",
    "2-0": "EVENT_YEAR",
    "3-0": "EVENT_MONTH",
    "4-0": "EVENT_DATE",
    "5-0": "EVENT_TIME",
    "6-0": "EVENT_TYPE",
    "7-0": "USER_ID",
    "8-0": "EMAIL",
    "9-0": "APP_ID",
    "10-0": "BRANCH_ID",
    "11-0": "DEPLOY_ID",
    "12-0": "SAVEPOINT_ID",
    "13-0": "SAVEPOINT_REVISION",
    "16-0": "DOMAIN",
    "17-0": "DATASTORE_ID",
    "18-0": "API_KEY_ID",
    "19-0": "NOTIFIER_ID",
    "20-0": "SAML_ID",
    "21-0": "WEBHOOK_ID",
    "22-0": "ADAPTER_ID",
    "23-0": "EMBED_ID",
    "24-0": "ROLE_ID",
    "25-0": "SERVICE",
    "26-0": "SERVICE_REVISION",
    "27-0": "LOGIN_TYPE",
    "28-0": "ROOT_SCOPE_USER_ID",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "NUMBER",
    "3-1": "DATE",
    "4-1": "DATE",
    "6-1": "VARCHAR",
    "7-1": "VARCHAR",
    "8-1": "VARCHAR",
    "9-1": "VARCHAR",
    "10-1": "VARCHAR",
    "11-1": "VARCHAR",
    "12-1": "VARCHAR",
    "13-1": "NUMBER",
    "14-0": "RESOURCE_TYPE",
    "15-0": "RESOURCE_ID",
    "14-1": "VARCHAR",
    "15-1": "VARCHAR",
    "16-1": "VARCHAR",
    "17-1": "VARCHAR",
    "18-1": "VARCHAR",
    "19-1": "VARCHAR",
    "20-1": "VARCHAR",
    "21-1": "VARCHAR",
    "22-1": "VARCHAR",
    "23-1": "VARCHAR",
    "24-1": "VARCHAR",
    "25-1": "VARCHAR",
    "26-1": "VARCHAR",
    "27-1": "VARCHAR",
    "28-1": "VARCHAR",
    "5-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 29
}
[/block]
## Branch

Basic data regarding application branches.

<details>
  <summary>How are application branches created and defined?</summary>

<br>

Branches in this context represent a linear log of application changes. Most branching of applications occurs whenever an application is deployed. When working directly in the Studio, the logistics of branching is handled under the hood. An application can be deployed, edited, and re-deployed to include the latest changes without the builder needing to consider how branching at all.

Under the hood, an application is forked each time it is deployed. The new version becomes published. It is also locked, or made uneditable, which prevents inadvertent changes from being made to a live app. Any changes made to the application in the Studio are made to the old, unpublished branch, which remains unlocked.

</details>
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "BRANCH_ID",
    "2-0": "APP_ID",
    "3-0": "DISPLAY_NAME",
    "4-0": "SOURCE_BRANCH_ID",
    "5-0": "SOURCE_BRANCH_REVISION",
    "6-0": "DESCRIPTION",
    "7-0": "CREATED_YEAR",
    "8-0": "CREATED_MONTH",
    "9-0": "CREATED_DATE",
    "10-0": "CREATED_TIME",
    "11-0": "MODIFIED_TIME",
    "12-0": "LOCK_TIME",
    "13-0": "USER_ID",
    "14-0": "FROZEN",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "VARCHAR",
    "5-1": "NUMBER",
    "6-1": "VARCHAR",
    "7-1": "NUMBER",
    "8-1": "DATE",
    "9-1": "DATE",
    "13-1": "VARCHAR",
    "14-1": "BOOLEAN",
    "10-1": "TIMESTAMPNTZ",
    "11-1": "TIMESTAMPNTZ",
    "12-1": "TIMESTAMPNTZ",
    "0-2": "Unique identifier of the [Organization](doc:airkit-organizations) the app was built in.",
    "1-2": "Unique identifier of the application branch.",
    "2-2": "Unique identifier of the application.",
    "7-2": "Year the branch was created.",
    "8-2": "Month the branch was created.",
    "9-2": "Date the branch was created.",
    "10-2": "Time the branch was created.",
    "11-2": "Time the branch was last modified.",
    "3-2": "Unique name of branch. A name is automatically generated upon the creation of each branch, and can be edited in the [Console](doc:console).",
    "4-2": "Unique identifier of the source branch.",
    "5-2": "Number of revisions from source branch. Count starts with source branch at 0.",
    "6-2": "Description of branch. A basic description is automatically generated upon the creation of each branch, and can be edited in the [Console](doc:console).",
    "12-2": "Time branch was locked, if applicable. Note that only locked branches can be deployed.",
    "14-2": "Whether branch is locked. ```TRUE``` means that it is, ```FALSE``` means that it isn't. Note that only locked branches can be deployed, and locked branches can't be edited.",
    "13-2": "Unique ID of the builder who created the branch."
  },
  "cols": 3,
  "rows": 15
}
[/block]
## Custom Metric

Data pertaining to when Custom Metrics occurred.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "CUSTOM_METRIC_KEY",
    "2-0": "FIRST_SEEN_TIME",
    "3-0": "LAST_SEEN_TIME",
    "4-0": "COUNT_FIRST_SEEN_TIME",
    "5-0": "COUNT_LAST_SEEN_TIME",
    "6-0": "STATISTIC_FIRST_SEEN_TIME",
    "7-0": "STATISTIC_LAST_SEEN_TIME",
    "8-0": "FIELD_FIRST_SEEN_TIME",
    "9-0": "FIELD_LAST_SEEN_TIME",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "TIMESTAMPNTZ",
    "3-1": "TIMESTAMPNTZ",
    "4-1": "TIMESTAMPNTZ",
    "5-1": "TIMESTAMPNTZ",
    "6-1": "TIMESTAMPNTZ",
    "7-1": "TIMESTAMPNTZ",
    "8-1": "TIMESTAMPNTZ",
    "9-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 10
}
[/block]
## Custom Metric Field

Basic data on which Custom Metrics have occurred.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "CUSTOM_METRIC_KEY",
    "2-0": "FIELD_VALUE",
    "3-0": "FIRST_SEEN_TIME",
    "3-1": "TIMESTAMPNTZ",
    "4-0": "LAST_SEEN_TIME",
    "4-1": "TIMESTAMPNTZ",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR"
  },
  "cols": 2,
  "rows": 5
}
[/block]
## Custom Metric Field Event

Data pertaining to the instance and value of Custom Metrics.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "SESSION_ID",
    "2-0": "EVENT_YEAR",
    "3-0": "EVENT_MONTH",
    "4-0": "EVENT_DATE",
    "5-0": "EVENT_TIME",
    "5-1": "TIMESTAMPNTZ",
    "6-0": "CUSTOM_METRIC_KEY",
    "7-0": "FIELD_VALUE",
    "8-0": "APP_ID",
    "9-0": "DEPLOY_ID",
    "10-0": "BRANCH_ID",
    "11-0": "EVENT_ID",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "NUMBER",
    "3-1": "DATE",
    "4-1": "DATE",
    "6-1": "VARCHAR",
    "7-1": "VARCHAR",
    "8-1": "VARCHAR",
    "9-1": "VARCHAR",
    "10-1": "VARCHAR",
    "11-1": "VARCHAR"
  },
  "cols": 2,
  "rows": 12
}
[/block]
## Custom Metric Info

Data pertaining to the circumstances under which Custom Metrics were logged.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "CUSTOM_METRIC_ID",
    "2-0": "APP_ID",
    "3-0": "BRANCH_ID",
    "4-0": "FIRST_SEEN_TIME",
    "5-0": "LAST_SEEN_TIME",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "6-0": "COUNT_FIRST_SEEN_TIME",
    "7-0": "COUNT_LAST_SEEN_TIME",
    "8-0": "STATISTIC_FIRST_SEEN_TIME",
    "9-0": "STATISTIC_FIRST_SEEN_TIME",
    "10-0": "FIELD_FIRST_SEEN_TIME",
    "11-0": "FIELD_LAST_SEEN_TIME",
    "4-1": "TIMESTAMPNTZ",
    "5-1": "TIMESTAMPNTZ",
    "6-1": "TIMESTAMPNTZ",
    "7-1": "TIMESTAMPNTZ",
    "8-1": "TIMESTAMPNTZ",
    "9-1": "TIMESTAMPNTZ",
    "10-1": "TIMESTAMPNTZ",
    "11-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 12
}
[/block]
## Custom Session Metric

Data summarizing the details of Custom Metrics.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "SESSION_ID",
    "2-0": "CUSTOM_METRIC_KEY",
    "3-0": "SESSION_YEAR",
    "4-0": "SESSION_MONTH",
    "5-0": "SESSION_DATE",
    "6-0": "SESSION_TIME",
    "7-0": "FIRST_TIMESTAMP",
    "8-0": "LAST_TIMESTAMP",
    "9-0": "APP_ID",
    "10-0": "DEPLOY_ID",
    "11-0": "BRANCH_ID",
    "12-0": "SAVEPOINT_REVISION",
    "13-0": "COUNT_COUNT",
    "14-0": "COUNT_FIRST_TIMESTAMP",
    "15-0": "COUNT_LAST_TIMESTAMP",
    "16-0": "STATISTIC_COUNT",
    "17-0": "STATISTIC_SUM",
    "18-0": "STATISTIC_MINIMUM",
    "19-0": "STATISTIC_MAXIMUM",
    "20-0": "STATISTIC_FIRST",
    "21-0": "STATISTIC_LAST",
    "22-0": "STATISTIC_FIRST_TIMESTAMP",
    "23-0": "STATISTIC_LAST_TIMESTAMP",
    "24-0": "FIELD_COUNT",
    "25-0": "FIELD_FIRST",
    "26-0": "FIELD_LAST",
    "27-0": "FIELD_FIRST_TIMESTAMP",
    "28-0": "FIELD_LAST_TIMESTAMP",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "NUMBER",
    "4-1": "DATE",
    "5-1": "DATE",
    "9-1": "VARCHAR",
    "10-1": "VARCHAR",
    "11-1": "VARCHAR",
    "12-1": "NUMBER",
    "13-1": "NUMBER",
    "6-1": "TIMESTAMPNTZ",
    "7-1": "TIMESTAMPNTZ",
    "8-1": "TIMESTAMPNTZ",
    "14-1": "TIMESTAMPNTZ",
    "15-1": "TIMESTAMPNTZ",
    "16-1": "NUMBER",
    "17-1": "NUMBER",
    "18-1": "NUMBER",
    "19-1": "NUMBER",
    "20-1": "NUMBER",
    "21-1": "NUMBER",
    "22-1": "TIMESTAMPNTZ",
    "23-1": "TIMESTAMPNTZ",
    "24-1": "NUMBER",
    "25-1": "VARCHAR",
    "26-1": "VARCHAR",
    "27-1": "TIMESTAMPNTZ",
    "28-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 29
}
[/block]
## Datastore

Basic information regarding each Datastore.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "DATASTORE_ID",
    "2-0": "DISPLAY_NAME",
    "3-0": "APP_ID",
    "4-0": "DEFAULT_TYPE",
    "5-0": "CREATED_YEAR",
    "6-0": "CREATED_MONTH",
    "7-0": "CREATED_DATE",
    "8-0": "CREATED_TIME",
    "8-1": "TIMESTAMPNTZ",
    "9-0": "MODIFIED_TIME",
    "9-1": "TIMESTAMPNTZ",
    "10-0": "DESCRIPTION",
    "10-1": "VARCHAR",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "VARCHAR",
    "5-1": "NUMBER",
    "6-1": "DATE",
    "7-1": "DATE"
  },
  "cols": 2,
  "rows": 11
}
[/block]
## Deployment

Basic data regarding application deployment.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "DEPLOYMENT_ID",
    "2-0": "DEPLOYMENT_KEY",
    "3-0": "DISPLAY_NAME",
    "4-0": "CREATED_YEAR",
    "5-0": "CREATED_MONTH",
    "6-0": "CREATED_DATE",
    "7-0": "CREATED_TIME",
    "8-0": "MODIFIED_TIME",
    "8-1": "TIMESTAMPNTZ",
    "7-1": "TIMESTAMPNTZ",
    "5-1": "DATE",
    "6-1": "DATE",
    "4-1": "NUMBER",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "9-0": "APP_ID",
    "10-0": "BRANCH_ID",
    "11-0": "USER_ID",
    "12-0": "PROFILE_ID",
    "13-0": "CXR_VERSION",
    "14-0": "DESCRIPTION",
    "15-0": "RESOURCE_BINDINGS",
    "16-0": "VARIABLES",
    "17-0": "NOTIFICATIONS",
    "18-0": "SHOW_PORTALS",
    "19-0": "PORTAL_NAME",
    "20-0": "RUN_PERIODIC_TASK",
    "9-1": "VARCHAR",
    "10-1": "VARCHAR",
    "11-1": "VARCHAR",
    "12-1": "VARCHAR",
    "13-1": "VARCHAR",
    "14-1": "VARCHAR",
    "15-1": "OBJECT",
    "16-1": "OBJECT",
    "17-1": "OBJECT",
    "18-1": "BOOLEAN",
    "19-1": "VARCHAR",
    "20-1": "BOOLEAN"
  },
  "cols": 2,
  "rows": 21
}
[/block]
## Funnel

Basic information on any Funnels that have been defined.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "SELECTOR_KEY",
    "2-0": "FUNNEL_KEY",
    "3-0": "FUNNEL_NAME",
    "4-0": "FUNNEL_DESCRIPTION",
    "5-0": "SELECTOR_NAME",
    "6-0": "SELECTOR_DESCRIPTION",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "VARCHAR",
    "5-1": "VARCHAR",
    "6-1": "VARCHAR"
  },
  "cols": 2,
  "rows": 7
}
[/block]
## Funnel Definition

Detailed information on how Funnels have been defined.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "FUNNEL_ID",
    "2-0": "FUNNEL_STAGE_KEY",
    "3-0": "DISPLAY_NAME",
    "4-0": "DESCRIPTION",
    "5-0": "FUNNEL_STEP",
    "6-0": "FUNNEL_NAME",
    "7-0": "SELECTOR_KEY",
    "8-0": "CREATED_TIME",
    "9-0": "MODIFIED_TIME",
    "10-0": "SELECTOR_FILTERS",
    "10-1": "VARIANT",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "VARCHAR",
    "5-1": "NUMBER",
    "6-1": "VARCHAR",
    "7-1": "VARCHAR",
    "8-1": "TIMESTAMPNTZ",
    "9-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 11
}
[/block]
## Invite

Data regarding sent invites to join an Organization.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "INVITE_ID",
    "2-0": "DISPLAY_NAME",
    "3-0": "EMAIL",
    "4-0": "STATUS",
    "5-0": "CREATED_YEAR",
    "6-0": "CREATED_MONTH",
    "7-0": "CREATED_DATE",
    "8-0": "CREATED_TIME",
    "9-0": "SENT_TIME",
    "10-0": "MODIFIED_TIME",
    "11-0": "USERNAME",
    "12-0": "VARIABLES",
    "13-0": "URL",
    "14-0": "ROLES",
    "15-0": "MULTIFACTOR",
    "16-0": "SSO_ONLY",
    "17-0": "FIRST_NAME",
    "18-0": "LAST_NAME",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "VARCHAR",
    "5-1": "NUMBER",
    "6-1": "DATE",
    "7-1": "DATE",
    "11-1": "VARCHAR",
    "12-1": "VARIANT",
    "13-1": "VARCHAR",
    "14-1": "VARIANT",
    "18-1": "VARCHAR",
    "17-1": "VARCHAR",
    "15-1": "BOOLEAN",
    "16-1": "BOOLEAN",
    "8-1": "TIMESTAMPNTZ",
    "9-1": "TIMESTAMPNTZ",
    "10-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 19
}
[/block]
## Metric Selector

Data defined by and generated from combing other metrics.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "SELECTOR_KEY",
    "2-0": "DISPLAY_NAME",
    "3-0": "STATUS",
    "4-0": "CREATED_TIME",
    "5-0": "MODIFIED_TIME",
    "6-0": "DESCRIPTION",
    "7-0": "STATUS_MESSAGE",
    "8-0": "APP_ID",
    "9-0": "BRANCH_ID",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "TIMESTAMPNTZ",
    "5-1": "TIMESTAMPNTZ",
    "6-1": "VARCHAR",
    "7-1": "VARCHAR",
    "8-1": "VARCHAR",
    "9-1": "VARCHAR"
  },
  "cols": 2,
  "rows": 10
}
[/block]
## Organization

Basic data pertaining to an Organization.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "DISPLAY_NAME",
    "2-0": "ORGANIZATION_KEY",
    "3-0": "REALM",
    "4-0": "WHITE_LABEL_ID",
    "5-0": "CREATED_YEAR",
    "6-0": "CREATED_MONTH",
    "7-0": "CREATED_DATE",
    "8-0": "CREATED_TIME",
    "9-0": "MODIFIED_TIME",
    "8-1": "TIMESTAMPNTZ",
    "9-1": "TIMESTAMPNTZ",
    "10-0": "SAML_METADATA_ID",
    "11-0": "LICENSE_KEY",
    "12-0": "ORGANIZATION_TYPE",
    "10-1": "VARCHAR",
    "12-1": "VARCHAR",
    "11-1": "VARCHAR",
    "6-1": "DATE",
    "7-1": "DATE",
    "5-1": "NUMBER",
    "0-1": "VARCHAR",
    "2-1": "VARCHAR",
    "1-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "VARCHAR"
  },
  "cols": 2,
  "rows": 13
}
[/block]
## Platform Event

Data pertaining to Events that take place beyond the scope of a Journey.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "EVENT_YEAR",
    "2-0": "EVENT_MONTH",
    "3-0": "EVENT_DATE",
    "4-0": "EVENT_TIME",
    "5-0": "EVENT_ID",
    "6-0": "APP_ID",
    "7-0": "BRANCH_ID",
    "8-0": "SAVEPOINT_REVISION",
    "9-0": "DEPLOY_ID",
    "10-0": "EVENT_TYPE",
    "11-0": "STATUS",
    "12-0": "MESSAGE",
    "13-0": "SERVICE",
    "14-0": "SERVICE_VERSION",
    "15-0": "CXR_VERSION",
    "16-0": "CONNECTION_ID",
    "17-0": "GROUP_ID",
    "18-0": "DURATION_MILLIS",
    "0-1": "VARCHAR",
    "1-1": "NUMBER",
    "2-1": "DATE",
    "3-1": "DATE",
    "4-1": "TIMESTAMPNTZ",
    "5-1": "VARCHAR",
    "6-1": "VARCHAR",
    "7-1": "VARCHAR",
    "8-1": "NUMBER",
    "9-1": "VARCHAR",
    "10-1": "VARCHAR",
    "11-1": "VARCHAR",
    "18-1": "NUMBER",
    "12-1": "VARCHAR",
    "13-1": "VARCHAR",
    "14-1": "VARCHAR",
    "15-1": "VARCHAR",
    "16-1": "VARCHAR",
    "17-1": "VARCHAR"
  },
  "cols": 2,
  "rows": 19
}
[/block]
## Resource

Data pertaining to external resources used within applications.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "RESOURCE_ID",
    "2-0": "DISPLAY_NAME",
    "3-0": "CREATED_YEAR",
    "4-0": "CREATED_MONTH",
    "5-0": "CREATED_DATE",
    "6-0": "CREATED_TIME",
    "7-0": "MODIFIED_TIME",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "NUMBER",
    "4-1": "DATE",
    "5-1": "DATE",
    "8-0": "REMOTE_TYPE",
    "8-1": "VARCHAR",
    "9-0": "REMOTE_ID",
    "9-1": "VARCHAR",
    "10-0": "DATA_SOURCE_ID",
    "10-1": "VARCHAR",
    "11-0": "CREDENTIAL_ID",
    "11-1": "VARCHAR",
    "12-0": "DOMAIN_ID",
    "12-1": "VARCHAR",
    "13-0": "URL_IDENTIFIER_ID",
    "13-1": "VARCHAR",
    "14-0": "PARENT_ID",
    "14-1": "VARCHAR",
    "15-0": "FROM_ADDRESS",
    "15-1": "VARCHAR",
    "16-0": "CAPABILITIES",
    "16-1": "OBJECT",
    "6-1": "TIMESTAMPNTZ",
    "7-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 17
}
[/block]
## Resource Deployment

Data pertaining to how resources were deployed.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "0-1": "VARCHAR",
    "1-0": "RESOURCE_DEPLOYMENT_ID",
    "1-1": "VARCHAR",
    "2-0": "RESOURCE_ID",
    "2-1": "VARCHAR",
    "3-0": "DEPLOYMENT_ID",
    "3-1": "VARCHAR",
    "4-0": "CREATED_YEAR",
    "4-1": "NUMBER",
    "5-0": "CREATED_MONTH",
    "5-1": "DATE",
    "6-0": "CREATED_DATE",
    "6-1": "DATE",
    "7-0": "CREATED_TIME",
    "8-0": "MODIFIED_TIME",
    "8-1": "TIMESTAMPNTZ",
    "7-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 9
}
[/block]
## Role

Data regarding roles with an Organization.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "ROLE_ID",
    "2-0": "FEATURES",
    "3-0": "DISPLAY_NAME",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "ARRAY",
    "3-1": "VARCHAR",
    "4-0": "DESCRIPTION",
    "4-1": "VARCHAR",
    "5-0": "CREATED_YEAR",
    "5-1": "NUMBER",
    "6-0": "CREATED_MONTH",
    "6-1": "DATE",
    "7-0": "CREATED_DATE",
    "7-1": "DATE",
    "8-0": "CREATED_TIME",
    "9-0": "MODIFIED_TIME",
    "10-0": "ROLE_RANK",
    "11-0": "ROLE_KEY",
    "10-1": "VARCHAR",
    "11-1": "VARCHAR",
    "8-1": "TIMESTAMPNTZ",
    "9-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 12
}
[/block]
## Session Event

Data pertaining to Events that take place within the Scope of a Journey.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "EVENT_YEAR",
    "2-0": "EVENT_MONTH",
    "3-0": "EVENT_DATE",
    "2-1": "DATE",
    "1-1": "NUMBER",
    "0-1": "VARCHAR",
    "3-1": "DATE",
    "4-0": "EVENT_TIME",
    "4-1": "TIMESTAMPNTZ",
    "5-0": "EVENT_ID",
    "5-1": "VARCHAR",
    "6-0": "APP_ID",
    "6-1": "VARCHAR",
    "7-0": "BRANCH_ID",
    "7-1": "VARCHAR",
    "8-0": "SESSION_ID",
    "8-1": "VARCHAR",
    "9-0": "DEPLOY_ID",
    "9-1": "VARCHAR",
    "10-0": "EVENT_TYPE",
    "10-1": "VARCHAR",
    "11-0": "CUSTOM_METRICS",
    "11-1": "OBJECT",
    "12-0": "DEFAULT_METRICS",
    "12-1": "OBJECT",
    "13-0": "SAVEPOINT_REVISION",
    "13-1": "NUMBER",
    "14-0": "CHANNEL_ID",
    "14-1": "VARCHAR",
    "15-0": "CHANNEL_KEY",
    "15-1": "VARCHAR",
    "16-0": "FLOW_ID",
    "16-1": "VARCHAR",
    "17-0": "ACTIVITY_ID",
    "17-1": "VARCHAR",
    "18-0": "ACTOR_ID",
    "18-1": "VARCHAR",
    "19-0": "RESOURCE_ID",
    "19-1": "VARCHAR",
    "20-0": "ACTIVITY_GROUP_ID",
    "20-1": "VARCHAR",
    "21-0": "CLIENT",
    "21-1": "VARCHAR",
    "22-0": "USER_AGENT",
    "22-1": "VARCHAR",
    "23-0": "SCREEN_WIDTH",
    "23-1": "NUMBER",
    "24-0": "SCREEN_HEIGHT",
    "24-1": "NUMBER",
    "25-0": "HTTP_SOURCE",
    "25-1": "VARCHAR",
    "26-0": "STATUS",
    "26-1": "VARCHAR",
    "27-0": "CODE",
    "27-1": "NUMBER",
    "28-0": "SERVICE",
    "28-1": "VARCHAR",
    "29-0": "SERVICE_VERSION",
    "29-1": "VARCHAR",
    "30-0": "EXTERNAL_ID",
    "30-1": "VARCHAR",
    "31-0": "DURATION_MILLIS",
    "31-1": "NUMBER",
    "32-0": "CXR_VERSION",
    "32-1": "VARCHAR",
    "33-0": "SOURCE_RUNTIME",
    "33-1": "VARCHAR",
    "34-0": "SOURCE_DETAIL",
    "34-1": "VARCHAR",
    "35-0": "APP_EVENT_PARENT_SCHEMA",
    "35-1": "VARCHAR",
    "36-0": "APP_EVENT_PARENT_ID",
    "36-1": "VARCHAR",
    "37-0": "APP_EVENT_SCHEMA",
    "37-1": "VARCHAR",
    "38-0": "APP_EVENT_ID",
    "38-1": "VARCHAR",
    "39-0": "CONTROL_ID",
    "39-1": "VARCHAR",
    "40-0": "CONTROL_SCHEMA",
    "40-1": "VARCHAR",
    "41-0": "TRIGGER_ID",
    "41-1": "VARCHAR",
    "42-0": "PROFILE_ID",
    "42-1": "VARCHAR",
    "43-0": "EVENT_SOURCE_ID",
    "43-1": "VARCHAR",
    "44-0": "ACTION_PARENT_PATH",
    "44-1": "VARCHAR",
    "45-0": "ACTION_PARENT_SCHEMA",
    "45-1": "VARCHAR",
    "46-0": "ACTION_PATH",
    "46-1": "VARCHAR",
    "47-0": "ACTION_SCHEMA",
    "47-1": "VARCHAR",
    "48-0": "CONNECTION_ID",
    "48-1": "VARCHAR",
    "49-0": "EVENT_SOURCE_NAME",
    "49-1": "VARCHAR",
    "50-0": "EVENT_SOURCE_PARENT_ID",
    "50-1": "VARCHAR",
    "51-0": "EVENT_HANDLER_ID",
    "51-1": "VARCHAR",
    "52-0": "EVENT_HANDLER_SCHEMA",
    "52-1": "VARCHAR",
    "53-0": "EVENT_SOURCE_INPUT",
    "53-1": "VARCHAR"
  },
  "cols": 2,
  "rows": 54
}
[/block]
## Session Funnel History

Data generated by defined Funnels.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "0-1": "VARCHAR",
    "1-0": "SESSION_ID",
    "1-1": "VARCHAR",
    "2-0": "FUNNEL_KEY",
    "2-1": "VARCHAR",
    "3-0": "FUNNEL_STAGE",
    "3-1": "VARCHAR",
    "4-0": "SELECTOR_KEY",
    "5-0": "SESSION_YEAR",
    "4-1": "VARCHAR",
    "5-1": "NUMBER",
    "6-0": "SESSION_MONTH",
    "6-1": "DATE",
    "7-0": "SESSION_DATE",
    "7-1": "DATE",
    "8-0": "SESSION_TIME",
    "9-0": "VISITED_TIME",
    "10-0": "VISITED_EVENT_ID",
    "10-1": "VARCHAR",
    "11-0": "APP_ID",
    "11-1": "VARCHAR",
    "12-0": "BRANCH_ID",
    "12-1": "VARCHAR",
    "13-0": "DEPTH_INTO_FUNNEL",
    "13-1": "NUMBER",
    "14-0": "FUNNEL_STAGE_STATUS",
    "14-1": "VARCHAR",
    "15-0": "IS_MATCHED",
    "15-1": "BOOLEAN",
    "16-0": "DURATION_HOURS",
    "16-1": "NUMBER",
    "17-0": "DURATION_MINUTES",
    "17-1": "NUMBER",
    "18-0": "DURATION_SECONDS",
    "18-1": "NUMBER",
    "19-0": "DURATION_MILLIS",
    "19-1": "NUMBER",
    "20-0": "LAST_UPDATED_TIME",
    "20-1": "TIMESTAMPNTZ",
    "8-1": "TIMESTAMPNTZ",
    "9-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 21
}
[/block]
## Session Summary

Data summarizing individual Journeys taken by users through all applications.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "SESSION_ID",
    "2-0": "APP_ID",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-0": "DEPLOY_ID",
    "3-1": "VARCHAR",
    "4-0": "BRANCH_ID",
    "4-1": "VARCHAR",
    "5-0": "SAVEPOINT_REVISION",
    "5-1": "NUMBER",
    "6-0": "SESSION_YEAR",
    "6-1": "NUMBER",
    "7-0": "SESSION_MONTH",
    "7-1": "DATE",
    "8-0": "SESSION_DATE",
    "8-1": "DATE",
    "9-0": "SESSION_TIME",
    "10-0": "FIRST_EVENT_TIME",
    "11-0": "FIRST_EVENT_ID",
    "11-1": "VARCHAR",
    "12-0": "LAST_EVENT_TIME",
    "13-0": "LAST_EVENT_ID",
    "13-1": "VARCHAR",
    "14-0": "START_EVENT_TIME",
    "15-0": "START_EVENT_ID",
    "15-1": "VARCHAR",
    "16-0": "END_EVENT_TIME",
    "17-0": "END_EVENT_ID",
    "17-1": "VARCHAR",
    "18-0": "ACTIONS_FIRED",
    "18-1": "NUMBER",
    "19-0": "EVENTS_OCCURRED",
    "19-1": "NUMBER",
    "20-0": "ERRORS_THROWN",
    "20-1": "NUMBER",
    "9-1": "TIMESTAMPNTZ",
    "10-1": "TIMESTAMPNTZ",
    "12-1": "TIMESTAMPNTZ",
    "14-1": "TIMESTAMPNTZ",
    "16-1": "TIMESTAMPNTZ",
    "21-0": "CONNECTIONS_RUN",
    "22-0": "TRIGGERS_REGISTERED",
    "23-0": "TRIGGERS_EXPIRED",
    "24-0": "TRIGGERS_INVOKED",
    "25-0": "VOICE_DURATION_HOURS",
    "26-0": "VOICE_DURATION_MINUTES",
    "27-0": "VOICE_DURATION_SECONDS",
    "28-0": "VOICE_DURATION_MILLIS",
    "29-0": "MESSAGES_SENT",
    "30-0": "MESSAGES_RECEIVED",
    "31-0": "VOICE_SENT",
    "32-0": "VOICE_RECEIVED",
    "33-0": "ACTION_RUNS",
    "34-0": "ACTION_ERRORS",
    "35-0": "RUNTIME_ERRORS",
    "36-0": "CANVAS_LINK_OPEN",
    "37-0": "MESSAGES_DELIVERED",
    "38-0": "MESSAGES_DELIVERY_FAILURES",
    "39-0": "SOCKET_CONNECTIONS",
    "40-0": "SOCKET_DISCONNECTIONS",
    "41-0": "HTTP_SOURCE",
    "41-1": "VARCHAR",
    "21-1": "NUMBER",
    "22-1": "NUMBER",
    "23-1": "NUMBER",
    "24-1": "NUMBER",
    "25-1": "NUMBER",
    "26-1": "NUMBER",
    "27-1": "NUMBER",
    "28-1": "NUMBER",
    "29-1": "NUMBER",
    "30-1": "NUMBER",
    "31-1": "NUMBER",
    "32-1": "NUMBER",
    "33-1": "NUMBER",
    "34-1": "NUMBER",
    "35-1": "NUMBER",
    "36-1": "NUMBER",
    "37-1": "NUMBER",
    "38-1": "NUMBER",
    "39-1": "NUMBER",
    "40-1": "NUMBER",
    "42-0": "BRIDGE_CALL_COMPLETIONS",
    "43-0": "BRIDGE_CALL_DURATION_HOURS",
    "44-0": "BRIDGE_CALL_DURATION_MINUTES",
    "45-0": "BRIDGE_CALL_DURATION_SECONDS",
    "46-0": "BRIDGE_CALL_DURATION_MILLIS",
    "47-0": "CALL_COMPLETIONS",
    "48-0": "CALL_DURATION_HOURS",
    "49-0": "CALL_DURATION_MINUTES",
    "50-0": "CALL_DURATION_SECONDS",
    "51-0": "CALL_DURATION_MILLIS",
    "52-0": "CXR_VERSION",
    "53-0": "USER_AGENT",
    "52-1": "VARCHAR",
    "53-1": "OBJECT",
    "54-0": "MIN_SCREEN_WIDTH",
    "55-0": "MIN_SCREEN_HEIGHT",
    "56-0": "MAX_SCREE_WIDTH",
    "57-0": "MAX_SCREEN_HEIGHT",
    "58-0": "APPLICATION_ERRORS",
    "59-0": "PLATFORM_ERRORS",
    "60-0": "MESSAGES_PENDING",
    "61-0": "EXTERNAL_IDENTIFIERS",
    "62-0": "BUILTIN_METRICS",
    "63-0": "CUSTOM_METRICS",
    "64-0": "DEFAULT_METRICS",
    "65-0": "SELECTOR_METRICS",
    "61-1": "ARRAY",
    "62-1": "OBJECT",
    "63-1": "OBJECT",
    "64-1": "OBJECT",
    "65-1": "OBJECT",
    "42-1": "NUMBER",
    "43-1": "NUMBER",
    "44-1": "NUMBER",
    "45-1": "NUMBER",
    "46-1": "NUMBER",
    "47-1": "NUMBER",
    "48-1": "NUMBER",
    "49-1": "NUMBER",
    "50-1": "NUMBER",
    "51-1": "NUMBER",
    "54-1": "NUMBER",
    "55-1": "NUMBER",
    "56-1": "NUMBER",
    "57-1": "NUMBER",
    "58-1": "NUMBER",
    "59-1": "NUMBER",
    "60-1": "NUMBER"
  },
  "cols": 2,
  "rows": 66
}
[/block]
## Session Trigger

Data pertaining to when and how Journeys are triggered.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "TRIGGER_ID",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "2-0": "TRIGGER_KEY",
    "3-0": "DISPLAY_NAME",
    "3-1": "VARCHAR",
    "4-0": "CREATED_YEAR",
    "4-1": "NUMBER",
    "5-0": "CREATED_MONTH",
    "5-1": "DATE",
    "6-0": "CREATED_DATE",
    "6-1": "DATE",
    "8-0": "MODIFIED_TIME",
    "7-0": "CREATED_TIME",
    "9-0": "EXECUTION_TIME",
    "10-0": "PROCESSED_TIME",
    "11-0": "TRIGGER_TYPE",
    "11-1": "VARCHAR",
    "12-0": "CALENDAR_RESTRICTION",
    "12-1": "VARCHAR",
    "13-0": "LAUNCH_BEHAVIOR",
    "13-1": "VARCHAR",
    "14-0": "CXR_VERSION",
    "14-1": "VARCHAR",
    "15-0": "DEPLOY_ID",
    "15-1": "VARCHAR",
    "16-0": "SESSION_ID",
    "16-1": "VARCHAR",
    "17-0": "ACTIVITY_GROUP_ID",
    "17-1": "VARCHAR",
    "18-0": "CHANNEL_ID",
    "18-1": "VARCHAR",
    "19-0": "EVENT_SOURCE_ID",
    "19-1": "VARCHAR",
    "20-0": "URL_IDENTIFIER_ID",
    "20-1": "VARCHAR",
    "21-0": "SHORT_ID",
    "21-1": "VARCHAR",
    "22-0": "SECURE_ID",
    "22-1": "VARCHAR",
    "23-0": "URL",
    "23-1": "VARCHAR",
    "7-1": "TIMESTAMPNTZ",
    "8-1": "TIMESTAMPNTZ",
    "9-1": "TIMESTAMPNTZ",
    "10-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 24
}
[/block]
## Trigger Resource

Basic data regarding the resources that trigger the start of Journeys. 
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "0-1": "VARCHAR",
    "1-0": "TRIGGER_RESOURCE_ID",
    "1-1": "VARCHAR",
    "2-0": "TRIGGER_ID",
    "2-1": "VARCHAR",
    "3-0": "RESOURCE_ID",
    "4-0": "DISPLAY_NAME",
    "5-0": "CREATED_TIME",
    "5-1": "TIMESTAMPNTZ",
    "6-0": "MODIFIED_TIME",
    "6-1": "TIMESTAMPNTZ",
    "3-1": "VARCHAR",
    "4-1": "VARCHAR"
  },
  "cols": 2,
  "rows": 7
}
[/block]
## User

Basic data pertaining to individual Builders. 
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "USER_ID",
    "2-0": "DISPLAY_NAME",
    "3-0": "EMAIL",
    "4-0": "EMAIL_VERIFIED",
    "5-0": "USERNAME",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "3-1": "VARCHAR",
    "4-1": "BOOLEAN",
    "5-1": "VARCHAR",
    "6-0": "CREATED_YEAR",
    "6-1": "NUMBER",
    "7-0": "CREATED_MONTH",
    "8-0": "CREATED_DATE",
    "9-0": "CREATED_TIME",
    "10-0": "MODIFIED_TIME",
    "7-1": "DATE",
    "8-1": "DATE",
    "11-0": "VARIABLES",
    "11-1": "VARIANT",
    "12-0": "MULTIFACTOR",
    "12-1": "BOOLEAN",
    "13-0": "PHONE_NUMER",
    "13-1": "VARIANT",
    "14-0": "FIRST_NAME",
    "15-0": "LAST_NAME",
    "14-1": "VARCHAR",
    "15-1": "VARCHAR",
    "9-1": "TIMESTAMPNTZ",
    "10-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 16
}
[/block]
## User Role

Data regarding the existing roles of Builders as well as when and if they were modified.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "0-1": "VARCHAR",
    "1-0": "USER_ID",
    "1-1": "VARCHAR",
    "2-0": "ROLE_ID",
    "2-1": "VARCHAR",
    "3-0": "CREATED_YEAR",
    "3-1": "NUMBER",
    "4-0": "CREATED_MONTH",
    "4-1": "DATE",
    "5-0": "CREATED_DATE",
    "5-1": "DATE",
    "6-0": "CREATED_TIME",
    "7-0": "MODIFIED_TIME",
    "6-1": "TIMESTAMPNTZ",
    "7-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 8
}
[/block]
## White Label

Basic data pertaining to a White Label Account.
[block:parameters]
{
  "data": {
    "h-0": "Property",
    "h-1": "Data Type",
    "0-0": "ORGANIZATION_ID",
    "1-0": "WHITE_LABEL_ID",
    "2-0": "DISPLAY_NAME",
    "3-0": "CREATED_YEAR",
    "3-1": "NUMBER",
    "4-0": "CREATED_MONTH",
    "4-1": "DATE",
    "5-0": "CREATED_DATE",
    "5-1": "DATE",
    "6-0": "CREATED_TIME",
    "7-0": "MODIFIED_TIME",
    "8-0": "FROM_EMAIL",
    "9-0": "FROM_PERSON",
    "0-1": "VARCHAR",
    "1-1": "VARCHAR",
    "2-1": "VARCHAR",
    "8-1": "VARCHAR",
    "9-1": "VARCHAR",
    "6-1": "TIMESTAMPNTZ",
    "7-1": "TIMESTAMPNTZ"
  },
  "cols": 2,
  "rows": 10
}
[/block]