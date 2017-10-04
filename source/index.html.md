---
title: RedEye DMS API 1.0.0
language_tabs:
  - shell: cURL
  
toc_footers:
  - <a href="https://app.redeyedms.com">See RedEye DMS for more information</a>
search: true
---

# RedEye DMS API 1.0.0
> ### Consumes
> `application/json`

> ### Produces
> `application/json`

**Schemes**: `https`

**Host**: `api.redeyedms.com`

**Base path**: `/`
### Authorization: api_key
Type | Name | In | Description
--- | --- | --- | ---
apiKey | Authorization | header | RedEye DMS API key from your bucket management interface.

## Search a bucket for artefacts

> Code sample

```shell
curl -X POST https://api.api.redeyedms.com/api/v1/search/ \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <YOUR_API_KEY' \
  -d '{
  "query": "",
  "advanced" :{
    "and" :[
      {
      "property": "title",
      "value": "demo"
      }
      ]
  }
}'
```

```http
POST //api/v1/search HTTP/1.1
Content-Type: application/json

{
    "advanced": {
        "and": [
            {
                "key_id": "string",
                "property": "string",
                "value": "string"
            }
        ],
        "or": [
            {
                "key_id": "string",
                "property": "string",
                "value": "string"
            }
        ],
        "not": [
            {
                "key_id": "string",
                "property": "string",
                "value": "string"
            }
        ]
    },
    "query": "string",
    "type": [
        "drawing",
        "document",
        "meida"
    ]
}
```

```http
HTTP/1.1 200 OK
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 401 Unauthorized
```

This will allow for searching for a buckets artefacts using Code, Title, metadata, etc and return upto 200 results. The limit and window can be set with query parameters.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
limit | query | integer | Optional. Limit of result set size, maximum 200
offset | query | integer | Optional. Offset into result set, must be less than total number of results
direction | query | string | Optional. Sort direction for result set, one of “asc” or “desc”
sort | query | string | Optional. Sort property for result set, one of “id”, “number”, “title”, “timestamp”
searchPayload<span title="required" class="required">&nbsp;*&nbsp;</span> | body | [SearchQuery](#searchquery) | Search query to run

### Responses
Http code | Type | Description
--- | --- | ---
200 | no content |
400 | no content |
401 | no content |


## Detailed Artefact data

> Code sample

```shell
curl -X GET https://api.api.redeyedms.com/api/v1/artefacts/{id} \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <YOUR_API_KEY'
```

```http
GET //api/v1/artefacts/{id} HTTP/1.1
```

```http
HTTP/1.1 200 OK
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 401 Unauthorized
```
```http
HTTP/1.1 404 Not Found
```

This will show detailed information about the artefact with the given identifier. If that artefact exisits in the bucket that the given api key can access.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | integer | The artefact ID

### Responses
Http code | Type | Description
--- | --- | ---
200 | no content |
400 | no content |
401 | no content |
404 | no content |


## Provides a download url for the native file

> Code sample

```shell
curl -X GET https://api.api.redeyedms.com/api/v1/artefacts/{id}/download \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <YOUR_API_KEY'
```

```http
GET //api/v1/artefacts/{id}/download HTTP/1.1
```

```http
HTTP/1.1 200 OK
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 401 Unauthorized
```
```http
HTTP/1.1 404 Not Found
```

This endpoint allows for the download of the latest "approved" native file for the artefact with the supplied identifier. If that artefact exisits in the bucket that the given api key can access.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | integer | The artefact ID

### Responses
Http code | Type | Description
--- | --- | ---
200 | no content |
400 | no content |
401 | no content |
404 | no content |


## Provides a download url for the previes file

> Code sample

```shell
curl -X GET https://api.api.redeyedms.com/api/v1/artefacts/{id}/preview \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <YOUR_API_KEY'
```

```http
GET //api/v1/artefacts/{id}/preview HTTP/1.1
```

```http
HTTP/1.1 200 OK
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 401 Unauthorized
```
```http
HTTP/1.1 404 Not Found
```

This endpoint allows for the download of the preview file for the artefact with the supplied identifier. If that artefact exisits in the bucket that the given api key can access.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | integer | The artefact ID

### Responses
Http code | Type | Description
--- | --- | ---
200 | no content |
400 | no content |
401 | no content |
404 | no content |


## Lists Groups for a bucket/site

> Code sample

```shell
curl -X GET https://api.api.redeyedms.com/api/v1/groups \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <YOUR_API_KEY'
```

```http
GET //api/v1/groups HTTP/1.1
```

```http
HTTP/1.1 200 OK
```
```http
HTTP/1.1 401 Unauthorized
```

This will show all groups for the bucket/site that you have access to from your api key.


### Responses
Http code | Type | Description
--- | --- | ---
200 | no content |
401 | no content |


## Shows Job status information

> Code sample

```shell
curl -X GET https://api.api.redeyedms.com/api/v1/jobs/{id} \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <YOUR_API_KEY'
```

```http
GET //api/v1/jobs/{id} HTTP/1.1
```

```http
HTTP/1.1 200 OK
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 401 Unauthorized
```
```http
HTTP/1.1 404 Not Found
```

This endpoint shows the current status of the job with the supplied identifier. If that job can be accesed with the given api key.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | integer | The artefact ID

### Responses
Http code | Type | Description
--- | --- | ---
200 | no content |
400 | no content |
401 | no content |
404 | no content |

## Lists Metadata keys for a bucket/site

> Code sample

```shell
curl -X GET https://api.api.redeyedms.com/api/v1/metdata \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <YOUR_API_KEY'
```

```http
GET //api/v1/metadata HTTP/1.1
```

```http
HTTP/1.1 200 OK
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 401 Unauthorized
```

This will show all available metadata for the bucket/site
that you have access to from your api key.


### Responses
Http code | Type | Description
--- | --- | ---
200 | no content |
400 | no content |
401 | no content |


## lists Metadata Keys for a bucket/site

> Code sample

```shell
curl -X GET https://api.api.redeyedms.com/api/v1/metadata/keys \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <YOUR_API_KEY'
```

```http
GET //api/v1/metadata/keys HTTP/1.1
```

```http
HTTP/1.1 200 OK
```
```http
HTTP/1.1 401 Unauthorized
```

This will show all available metadata for the bucket/site
that you have access to from your api key.


### Responses
Http code | Type | Description
--- | --- | ---
200 | no content |
401 | no content |


## Create a new print job

> Code Sample

```shell
curl -X POST \
  https://api.redeyedms.com/api/v1/print \
  -H 'authorization: Bearer <YOUR_API_KEY' \
  -H 'content-type: application/json' \
  -d '{
    "artefacts": [
    	{"id": ARTEFACT_ID}
    ]
}'
```

```http
POST //api/v1/print HTTP/1.1
```

```http
HTTP/1.1 202 Accepted
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 401 Unauthorized
```

This allows for a print job to be created.


### Responses
Http code | Type | Description
--- | --- | ---
202 | no content |
400 | no content |
401 | no content |


## Get information about a print job

> Code sample

```shell
curl -X GET https://api.api.redeyedms.com/api/v1/print/{id} \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <YOUR_API_KEY'
```

```http
GET //api/v1/print/{id} HTTP/1.1
```

```http
HTTP/1.1 200 OK
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 401 Unauthorized
```
```http
HTTP/1.1 404 Not Found
```

This will show information about a print job. On completion it will provide a download link for the print job zip file.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | integer | The print job ID

### Responses
Http code | Type | Description
--- | --- | ---
200 | no content |
400 | no content |
401 | no content |
404 | no content |



# Models
## Error
```json
{
    "code": "string",
    "message": "string"
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
code<span title="required" class="required">&nbsp;*&nbsp;</span> | string |  |
message<span title="required" class="required">&nbsp;*&nbsp;</span> | string |  |


## Artefact
```json
{
    "code": "string",
    "created": "object",
    "current_revision_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "currentfilecontent_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "discr": "string",
    "fold_ignored": "boolean",
    "id": "integer",
    "metadata_set_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "number": "boolean",
    "parent_artefact": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "policy_date": "object",
    "record_policy_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "siteId": "integer",
    "srtefact_status_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "state": {
        "String": "string",
        "Valid": "boolean"
    },
    "title": {
        "String": "string",
        "Valid": "boolean"
    }
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
code | string |  |
created | object |  |
current_revision_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
currentfilecontent_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
discr | string |  |
fold_ignored | boolean |  |
id | integer | int64 |
metadata_set_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
number | boolean |  |
parent_artefact | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
policy_date | object |  |
record_policy_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
siteId | integer | int64 |
srtefact_status_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
state | NullString |  | NullString represents a string that may be null.
title | NullString |  | NullString represents a string that may be null.


## SearchQuery
```json
{
    "advanced": {
        "and": [
            {
                "key_id": "string",
                "property": "string",
                "value": "string"
            }
        ],
        "or": [
            {
                "key_id": "string",
                "property": "string",
                "value": "string"
            }
        ],
        "not": [
            {
                "key_id": "string",
                "property": "string",
                "value": "string"
            }
        ]
    },
    "query": "string",
    "type": [
        "string"
    ]
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
advanced | object |  |
query | string |  |
type | array[string] |  |


## SearchProperty
```json
{
    "key_id": "string",
    "property": "string",
    "value": "string"
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
key_id | string |  |
property | string |  |
value | string |  |


## ArtefactLink
```json
{
    "id": "integer",
    "url": "string"
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
id | integer | int64 | The artefact id
url | string |  | Time sensitive presigned url to get the file.


## Group
```json
{
    "id": "integer",
    "name": "string"
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
id | integer | int64 |
name | string |  |


## Ids
```json
{
    "id": "integer"
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
id | integer | int64 |


## Job
```json
{
    "artefacts": [
        {
            "id": "integer"
        }
    ],
    "file": "string",
    "id": "integer"
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
artefacts | array[[Ids](#ids)] |  |
file | string |  |
id | integer | int64 |


## Location
```json
{
    "lat": "string",
    "lon": "string"
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
lat | number | float |
lon | number | float |


## Metadata
```json
{
    "key_id": "integer",
    "key_name": "string",
    "value": "string"
}
```

Metadata is a catch all key/value pairing to add information about an artefact.


### Fields
Name | Type | Format | Description
--- | --- | --- | ---
key_id | integer |  |
key_name | string |  |
value | string |  |


## MetadataKey
```json
{
    "id": "integer",
    "description": "string",
    "name": "string"
}
```

Metadata Key for use in the Search Endpoint


### Fields
Name | Type | Format | Description
--- | --- | --- | ---
id<span title="required" class="required">&nbsp;*&nbsp;</span> | integer | int64 | ID of the metadata key to use in the search endpoint
description | string |  | A user friendly description of the metadata key
name<span title="required" class="required">&nbsp;*&nbsp;</span> | string |  | A user friendly name of the metadata key


## Revision
```json
{
    "VersionNumber": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "approvalrequest_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "artefact_code": {
        "String": "string",
        "Valid": "boolean"
    },
    "artefact_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "artefactstatus_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "currentmetadataset_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "id": "integer",
    "name": {
        "String": "string",
        "Valid": "boolean"
    },
    "parent_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "priority": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "project_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "revisionstatus_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "site_id": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "title": {
        "String": "string",
        "Valid": "boolean"
    }
}
```

Revision is the information about a revision of an artefact


### Fields
Name | Type | Format | Description
--- | --- | --- | ---
VersionNumber | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
approvalrequest_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
artefact_code | NullString |  | NullString represents a string that may be null.
artefact_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
artefactstatus_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
currentmetadataset_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
id | integer | int64 |
name | NullString |  | NullString represents a string that may be null.
parent_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
priority | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
project_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
revisionstatus_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
site_id | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
title | NullString |  | NullString represents a string that may be null.


## RevisionStatus
```json
{
    "ApprovalRequestRd": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "Comment": {
        "String": "string",
        "Valid": "boolean"
    },
    "FileId": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "Id": "integer",
    "ParentRevisionStatusId": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "ReminderSent": "boolean",
    "RevisionId": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "RevisionStatusTypeId": {
        "Int64": "integer",
        "Valid": "boolean"
    },
    "Timestamp": "object",
    "UserId": "integer",
    "WorkflowStepId": {
        "Int64": "integer",
        "Valid": "boolean"
    }
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
ApprovalRequestRd | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
Comment | NullString |  | NullString represents a string that may be null.
FileId | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
Id | integer | int64 |
ParentRevisionStatusId | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
ReminderSent | boolean |  |
RevisionId | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
RevisionStatusTypeId | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.
Timestamp | object |  |
UserId | integer | int64 |
WorkflowStepId | NullInt64 |  | NullInt64 is a 64 bit Integer that might be Null in the datastore.


## Status
```json
{
    "complete": "boolean",
    "status": "string",
    "type": "string"
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
complete | boolean |  |
status | string |  |
type | string |  |


## StatusType
```json
{
    "Hidden": "boolean",
    "Id": "integer",
    "Name": "string",
    "NotificationType": {
        "String": "string",
        "Valid": "boolean"
    },
    "Revised": "boolean",
    "TypeName": {
        "String": "string",
        "Valid": "boolean"
    },
    "Watermark": "boolean"
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
Hidden | boolean |  |
Id | integer | int64 |
Name | string |  |
NotificationType | NullString |  | NullString represents a string that may be null.
Revised | boolean |  |
TypeName | NullString |  | NullString represents a string that may be null.
Watermark | boolean |  |


## ValidationErrorResponse
```json
{
    "Body": {
        "Message": "string"
    }
}
```

### Fields
Name | Type | Format | Description
--- | --- | --- | ---
Body | object |  | The error message<br/>in: body


# More Information

For more information please contact your RedEye Customer Success Manager or email RedEye support at <support@redeye.co>

<style>
    ul.enum {
        margin: 0;
        padding: 0 0 0 2px;
        list-style-position: inside;
    }
    .required {
        color: red;
        font-weight: bold;
    }
    a.pseudo {
        border-bottom:1px dashed;
        text-decoration: none;
    }
</style>
