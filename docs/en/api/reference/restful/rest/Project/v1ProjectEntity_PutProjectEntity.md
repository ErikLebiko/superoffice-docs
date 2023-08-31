---
title: PUT Project/{id}
uid: v1ProjectEntity_PutProjectEntity
generated: true
---

# PUT Project/{id}

```http
PUT /api/v1/Project/{id}
```

Updates the existing ProjectEntity






| Path Part | Type | Description |
|-----------|------|-------------|
| id | int32 | The ProjectEntity id to update. **Required** |


## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category" Default = show all fields. |

```http
PUT /api/v1/Project/{id}?$select=name,department,category/id
```


## Request Headers

| Parameter Name | Description |
|----------------|-------------|
| Authorization  | Supports 'Basic', 'SoTicket' and 'Bearer' schemes, depending on installation type. |
| X-XSRF-TOKEN   | If not using Authorization header, you must provide XSRF value from cookie or hidden input field |
| Content-Type | Content-type of the request body: `application/json`, `text/json`, `application/xml`, `text/xml`, `application/x-www-form-urlencoded`, `application/json-patch+json`, `application/merge-patch+json` |
| Accept         | Content-type(s) you would like the response in: `application/json`, `text/json`, `application/xml`, `text/xml`, `application/json-patch+json`, `application/merge-patch+json` |
| Accept-Language | Convert string references and multi-language values into a specified language (iso2) code. |
| SO-Language | Convert string references and multi-language values into a specified language (iso2) code. Overrides Accept-Language value. |
| SO-Culture | Number, date formatting in a specified culture (iso2 language) code. Partially overrides SO-Language/Accept-Language value. Ignored if no Language set. |
| SO-TimeZone | Specify the timezone code that you would like date/time responses converted to. |
| SO-AppToken | The application token that identifies the partner app. Used when calling Online WebAPI from a server. |

## Request Body: entity 

The ProjectEntity to be saved. 

| Property Name | Type |  Description |
|----------------|------|--------------|
| ProjectId | Integer | Primary key |
| Name | String | Project name |
| ProjectNumber | String | Automatically generated number |
| ProjectMembers | Array | The persons which are members of the project |
| Urls | Array | The project's internet adresses |
| CreatedDate | String | Registered date  in UTC. |
| UpdatedDate | String | Last updated date  in UTC. |
| Description | String | The actual text, max 2047 significant characters even though it is stored as a larger data type on some databases |
| Postit | String | The actual text, max 2047 significant characters even though it is stored as a larger data type on some databases |
| CreatedBy | Associate | The person that created the project |
| UpdatedBy | Associate | The person that last updated the project |
| Associate | Associate | The person that created the project  <para>Use MDO List name "associate" to get list items.</para> |
| ProjectStatus | ProjectStatus | Project status is a list defined by the database administrator. Different statuses of a project may be: “In planning”, “Started”, “Finished” and so on  <para>Use MDO List name "projectstatus" to get list items.</para> |
| ProjectType | ProjectType | Project type is a list defined by the database admin. for example: 'Large', 'Small', 'Party'...  <para>Use MDO List name "projecttype" to get list items.</para> |
| HasImage | Boolean | True if the project has an image. (This is the image that is displayed in the CRM client) |
| ImageDescription | String | Description of the project image if it exists. (This is the image that is displayed in the CRM client) |
| ActiveStatusMonitorId | Integer | Active status monitor identity with the lowest rank for project |
| Links | Array | List of all elements linked to the project |
| ActiveLinks | Integer | Number of active links to documents, other appointments, and such |
| Completed | Boolean | Done (0=false, 1=true). Status implies changes in which fields are shown in GUI, as well as which fields can be updated |
| NextMilestoneDate | String | Calculated date, reflects date of closest non-complete future milestone activity |
| NmdAppointmentId | Integer | ID of appointment that "caused" the nextMilestoneDate, can be 0 |
| EndDate | String | Planned end date for project, inhertied from type and later editable |
| ActiveErpLinks | Integer | The number of active erp links |
| UserDefinedFields | Object | Deprecated: Use {SuperOffice.CRM.Services.ProjectEntity.CustomFields} instead. Dictionary of user defined field data. The key string is the ProgId of the UdefField, or if the ProgId is empty it is a string of the format "SuperOffice:[UdefFieldIdentity]", e.g. "SuperOffice:1234" |
| ExtraFields | Object | Deprecated: Use {SuperOffice.CRM.Services.ProjectEntity.CustomFields} instead. Extra fields added to the carrier. This could be data from Plug-ins, the foreign key system, external applications, etc. |
| CustomFields | Object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.ProjectEntity.ExtraFields} and <see cref="P:SuperOffice.CRM.Services.ProjectEntity.UserDefinedFields">UserDefinedFields</see> properties are deprecated in favor of this combined collection. |
| PublishEventDate | String | Publish event date |
| PublishTo | String | Publication valid to (inclusive) |
| PublishFrom | String | Publication valid from (inclusive) |
| IsPublished | Boolean | Publication is published |

## Response:

ProjectEntity updated.

| Response | Description |
|----------------|-------------|
| 200 | ProjectEntity updated. |
| 412 | Update stopped because ProjectEntity has changed since the requested If-Unmodified-Since timestamp. |
| 400 | Bad request. Entity to save is not in request body. |

### Response body: ProjectEntityWithLinks

| Property Name | Type |  Description |
|----------------|------|--------------|
| ProjectId | int32 | Primary key |
| Name | string | Project name |
| ProjectNumber | string | Automatically generated number |
| ProjectMembers | array | The persons which are members of the project |
| Urls | array | The project's internet adresses |
| CreatedDate | date-time | Registered date  in UTC. |
| UpdatedDate | date-time | Last updated date  in UTC. |
| Description | string | The actual text, max 2047 significant characters even though it is stored as a larger data type on some databases |
| Postit | string | The actual text, max 2047 significant characters even though it is stored as a larger data type on some databases |
| CreatedBy | Associate | The person that created the project |
| UpdatedBy | Associate | The person that last updated the project |
| Associate | Associate | The person that created the project  <para>Use MDO List name "associate" to get list items.</para> |
| ProjectStatus | ProjectStatus | Project status is a list defined by the database administrator. Different statuses of a project may be: “In planning”, “Started”, “Finished” and so on  <para>Use MDO List name "projectstatus" to get list items.</para> |
| ProjectType | ProjectType | Project type is a list defined by the database admin. for example: 'Large', 'Small', 'Party'...  <para>Use MDO List name "projecttype" to get list items.</para> |
| HasImage | bool | True if the project has an image. (This is the image that is displayed in the CRM client) |
| ImageDescription | string | Description of the project image if it exists. (This is the image that is displayed in the CRM client) |
| ActiveStatusMonitorId | int32 | Active status monitor identity with the lowest rank for project |
| Links | array | List of all elements linked to the project |
| ActiveLinks | int32 | Number of active links to documents, other appointments, and such |
| Completed | bool | Done (0=false, 1=true). Status implies changes in which fields are shown in GUI, as well as which fields can be updated |
| NextMilestoneDate | date-time | Calculated date, reflects date of closest non-complete future milestone activity |
| NmdAppointmentId | int32 | ID of appointment that "caused" the nextMilestoneDate, can be 0 |
| EndDate | date-time | Planned end date for project, inhertied from type and later editable |
| ActiveErpLinks | int32 | The number of active erp links |
| UserDefinedFields | object | Deprecated: Use {SuperOffice.CRM.Services.ProjectEntity.CustomFields} instead. Dictionary of user defined field data. The key string is the ProgId of the UdefField, or if the ProgId is empty it is a string of the format "SuperOffice:[UdefFieldIdentity]", e.g. "SuperOffice:1234" |
| ExtraFields | object | Deprecated: Use {SuperOffice.CRM.Services.ProjectEntity.CustomFields} instead. Extra fields added to the carrier. This could be data from Plug-ins, the foreign key system, external applications, etc. |
| CustomFields | object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.ProjectEntity.ExtraFields} and <see cref="P:SuperOffice.CRM.Services.ProjectEntity.UserDefinedFields">UserDefinedFields</see> properties are deprecated in favor of this combined collection. |
| PublishEventDate | date-time | Publish event date |
| PublishTo | date-time | Publication valid to (inclusive) |
| PublishFrom | date-time | Publication valid from (inclusive) |
| IsPublished | bool | Publication is published |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |
| _Links | object |  |

## Sample request

```http!
PUT /api/v1/Project/{id}
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: en
Content-Type: application/json; charset=utf-8

{
  "ProjectId": 37,
  "Name": "Hudson-Stanton",
  "ProjectNumber": "1240870",
  "ProjectMembers": [
    {
      "ProjectmemberId": 317,
      "ContactId": 704,
      "ProjectId": 777,
      "ContactName": "Dietrich-Abernathy",
      "ContactDepartment": "",
      "ProjectName": "Eichmann, Labadie and Schuppe",
      "EmailId": 148,
      "EmailAddress": "larue@torp.ca",
      "CountryId": 493,
      "Firstname": "Lorenz",
      "MiddleName": "Renner-Heller",
      "Lastname": "Hilll",
      "PersonId": 915,
      "Mrmrs": "velit",
      "ProjectMemberTypeName": "Batz LLC",
      "Phone": "(394)547-4369 x567",
      "PhoneId": 230,
      "ProjectMemberTypeId": 180,
      "EmailAddressName": "zion@gislasonmueller.com",
      "Comment": "iusto",
      "FullName": "Mrs. Chad Ashtyn Gibson I"
    }
  ],
  "Urls": [
    {
      "Value": "perferendis",
      "StrippedValue": "totam",
      "Description": "Up-sized clear-thinking attitude"
    },
    {
      "Value": "perferendis",
      "StrippedValue": "totam",
      "Description": "Up-sized clear-thinking attitude"
    }
  ],
  "CreatedDate": "2022-04-29T03:31:32.769495+02:00",
  "UpdatedDate": "1996-12-26T03:31:32.769495+01:00",
  "Description": "Organized intangible migration",
  "Postit": "eveniet",
  "CreatedBy": null,
  "UpdatedBy": null,
  "Associate": null,
  "ProjectStatus": null,
  "ProjectType": null,
  "HasImage": false,
  "ImageDescription": "Intuitive actuating contingency",
  "ActiveStatusMonitorId": 368,
  "Links": [
    {
      "EntityName": "Kemmer Inc and Sons",
      "Id": 169,
      "Description": "Fundamental non-volatile knowledge base",
      "ExtraInfo": "ea",
      "LinkId": 8
    },
    {
      "EntityName": "Kemmer Inc and Sons",
      "Id": 169,
      "Description": "Fundamental non-volatile knowledge base",
      "ExtraInfo": "ea",
      "LinkId": 8
    }
  ],
  "ActiveLinks": 839,
  "Completed": false,
  "NextMilestoneDate": "2006-04-26T03:31:32.769495+02:00",
  "NmdAppointmentId": 948,
  "EndDate": "2022-05-06T03:31:32.769495+02:00",
  "ActiveErpLinks": 612,
  "UserDefinedFields": {
    "SuperOffice:1": "Santiago Homenick",
    "SuperOffice:2": "True"
  },
  "ExtraFields": {
    "ExtraFields1": "eligendi",
    "ExtraFields2": "quae"
  },
  "CustomFields": {
    "CustomFields1": "amet",
    "CustomFields2": "ut"
  },
  "PublishEventDate": "2010-09-09T03:31:32.769495+02:00",
  "PublishTo": "2022-07-13T03:31:32.769495+02:00",
  "PublishFrom": "1998-03-01T03:31:32.769495+01:00",
  "IsPublished": false
}
```

## Sample response

```http_
HTTP/1.1 200 ProjectEntity updated.
Content-Type: application/json; charset=utf-8

{
  "ProjectId": 962,
  "Name": "Crona Group",
  "ProjectNumber": "374865",
  "ProjectMembers": [
    {
      "ProjectmemberId": 568,
      "ContactId": 34,
      "ProjectId": 972,
      "ContactName": "Bednar-Kiehn",
      "ContactDepartment": "",
      "ProjectName": "Rau, Beahan and Abshire",
      "EmailId": 535,
      "EmailAddress": "cayla_hand@cartercummings.name",
      "CountryId": 10,
      "Firstname": "Fredy",
      "MiddleName": "Huel, Beatty and Hyatt",
      "Lastname": "Kreiger",
      "PersonId": 608,
      "Mrmrs": "minus",
      "ProjectMemberTypeName": "Carroll, Orn and Champlin",
      "Phone": "438-916-7629",
      "PhoneId": 818,
      "ProjectMemberTypeId": 235,
      "EmailAddressName": "laverna_romaguera@oconnell.info",
      "Comment": "natus",
      "FullName": "Garnett Boyle II",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 270
        }
      }
    }
  ],
  "Urls": [
    {
      "Value": "et",
      "StrippedValue": "saepe",
      "Description": "Open-source bi-directional solution",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 99
        }
      }
    },
    {
      "Value": "et",
      "StrippedValue": "saepe",
      "Description": "Open-source bi-directional solution",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 99
        }
      }
    }
  ],
  "CreatedDate": "1999-08-24T03:31:32.769495+02:00",
  "UpdatedDate": "2014-05-11T03:31:32.769495+02:00",
  "Description": "Expanded holistic protocol",
  "Postit": "ut",
  "CreatedBy": null,
  "UpdatedBy": null,
  "Associate": null,
  "ProjectStatus": null,
  "ProjectType": null,
  "HasImage": false,
  "ImageDescription": "Polarised hybrid budgetary management",
  "ActiveStatusMonitorId": 23,
  "Links": [
    {
      "EntityName": "Wuckert, Roob and Reilly",
      "Id": 305,
      "Description": "Configurable needs-based monitoring",
      "ExtraInfo": "ipsa",
      "LinkId": 719,
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 221
        }
      }
    }
  ],
  "ActiveLinks": 183,
  "Completed": false,
  "NextMilestoneDate": "2008-02-20T03:31:32.769495+01:00",
  "NmdAppointmentId": 909,
  "EndDate": "1999-11-16T03:31:32.769495+01:00",
  "ActiveErpLinks": 204,
  "UserDefinedFields": {
    "SuperOffice:1": "Dina Wilderman",
    "SuperOffice:2": "True"
  },
  "ExtraFields": {
    "ExtraFields1": "consequuntur",
    "ExtraFields2": "assumenda"
  },
  "CustomFields": {
    "CustomFields1": "sit",
    "CustomFields2": "similique"
  },
  "PublishEventDate": "2007-08-24T03:31:32.769495+02:00",
  "PublishTo": "2000-03-06T03:31:32.769495+01:00",
  "PublishFrom": "2010-01-09T03:31:32.769495+01:00",
  "IsPublished": false,
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 292
    }
  },
  "_Links": {
    "Self": "https://www.example.com/api/v1/project/321",
    "Archive": "https://www.example.com/api/v1/project"
  }
}
```