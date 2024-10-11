---
title: POST Project
uid: v1ProjectEntity_PostProjectEntity
generated: true
---

# POST Project

```http
POST /api/v1/Project
```

Creates a new ProjectEntity


Calls the Project agent service SaveProjectEntity.






## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category" Default = show all fields. |

```http
POST /api/v1/Project?$select=name,department,category/id
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

## Request Body: newEntity 

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

OK

| Response | Description |
|----------------|-------------|
| 200 | OK |

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
| Associate | Associate | The person that created the project  Use MDO List name "associate" to get list items. |
| ProjectStatus | ProjectStatus | Project status is a list defined by the database administrator. Different statuses of a project may be: “In planning”, “Started”, “Finished” and so on  Use MDO List name "projectstatus" to get list items. |
| ProjectType | ProjectType | Project type is a list defined by the database admin. for example: 'Large', 'Small', 'Party'...  Use MDO List name "projecttype" to get list items. |
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
| CustomFields | object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.ProjectEntity.ExtraFields} and UserDefinedFields properties are deprecated in favor of this combined collection. |
| PublishEventDate | date-time | Publish event date |
| PublishTo | date-time | Publication valid to (inclusive) |
| PublishFrom | date-time | Publication valid from (inclusive) |
| IsPublished | bool | Publication is published |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |
| _Links | object |  |

## Sample request

```http!
POST /api/v1/Project
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: en
Content-Type: application/json; charset=utf-8

{
  "ProjectId": 913,
  "Name": "Nader, Larson and Bradtke",
  "ProjectNumber": "1125185",
  "ProjectMembers": [
    {
      "ProjectmemberId": 441,
      "ContactId": 979,
      "ProjectId": 706,
      "ContactName": "Reynolds Inc and Sons",
      "ContactDepartment": "",
      "ProjectName": "Heathcote LLC",
      "EmailId": 10,
      "EmailAddress": "orlando.walker@andersonbins.com",
      "CountryId": 574,
      "Firstname": "Lambert",
      "MiddleName": "Bayer Inc and Sons",
      "Lastname": "Rutherford",
      "PersonId": 326,
      "Mrmrs": "delectus",
      "ProjectMemberTypeName": "Buckridge LLC",
      "Phone": "(112)111-9888 x03064",
      "PhoneId": 729,
      "ProjectMemberTypeId": 868,
      "EmailAddressName": "greg@hoeger.info",
      "Comment": "amet",
      "FullName": "Gayle Hartmann"
    }
  ],
  "Urls": [
    {
      "Value": "enim",
      "StrippedValue": "molestiae",
      "Description": "Networked demand-driven paradigm"
    },
    {
      "Value": "enim",
      "StrippedValue": "molestiae",
      "Description": "Networked demand-driven paradigm"
    }
  ],
  "CreatedDate": "2006-02-14T03:44:57.453141+01:00",
  "UpdatedDate": "2013-08-24T03:44:57.453141+02:00",
  "Description": "Inverse exuding conglomeration",
  "Postit": "consectetur",
  "CreatedBy": null,
  "UpdatedBy": null,
  "Associate": null,
  "ProjectStatus": null,
  "ProjectType": null,
  "HasImage": false,
  "ImageDescription": "Assimilated radical initiative",
  "ActiveStatusMonitorId": 951,
  "Links": [
    {
      "EntityName": "Balistreri LLC",
      "Id": 902,
      "Description": "Switchable composite protocol",
      "ExtraInfo": "eum",
      "LinkId": 787
    },
    {
      "EntityName": "Balistreri LLC",
      "Id": 902,
      "Description": "Switchable composite protocol",
      "ExtraInfo": "eum",
      "LinkId": 787
    }
  ],
  "ActiveLinks": 123,
  "Completed": true,
  "NextMilestoneDate": "1999-04-12T03:44:57.453141+02:00",
  "NmdAppointmentId": 639,
  "EndDate": "2008-12-26T03:44:57.453141+01:00",
  "ActiveErpLinks": 644,
  "UserDefinedFields": {
    "SuperOffice:1": "Ms. Alf Izabella McGlynn I",
    "SuperOffice:2": "1227213247"
  },
  "ExtraFields": {
    "ExtraFields1": "ut",
    "ExtraFields2": "voluptatem"
  },
  "CustomFields": {
    "CustomFields1": "repudiandae",
    "CustomFields2": "est"
  },
  "PublishEventDate": "2020-08-12T03:44:57.453141+02:00",
  "PublishTo": "2005-06-21T03:44:57.453141+02:00",
  "PublishFrom": "1998-09-06T03:44:57.453141+02:00",
  "IsPublished": true
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "ProjectId": 952,
  "Name": "Cronin LLC",
  "ProjectNumber": "1347241",
  "ProjectMembers": [
    {
      "ProjectmemberId": 758,
      "ContactId": 140,
      "ProjectId": 844,
      "ContactName": "Herman-Kilback",
      "ContactDepartment": "",
      "ProjectName": "Sawayn, DuBuque and Ebert",
      "EmailId": 899,
      "EmailAddress": "marge_wisoky@hauck.com",
      "CountryId": 869,
      "Firstname": "Ethyl",
      "MiddleName": "Marks Inc and Sons",
      "Lastname": "Lynch",
      "PersonId": 192,
      "Mrmrs": "ipsum",
      "ProjectMemberTypeName": "Franecki, Bins and Torphy",
      "Phone": "1-231-140-8037",
      "PhoneId": 369,
      "ProjectMemberTypeId": 722,
      "EmailAddressName": "filomena@watsica.ca",
      "Comment": "aut",
      "FullName": "Jerrod Bednar PhD",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 102
        }
      }
    }
  ],
  "Urls": [
    {
      "Value": "voluptatem",
      "StrippedValue": "sunt",
      "Description": "Versatile foreground secured line",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 890
        }
      }
    },
    {
      "Value": "voluptatem",
      "StrippedValue": "sunt",
      "Description": "Versatile foreground secured line",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 890
        }
      }
    }
  ],
  "CreatedDate": "2014-11-29T03:44:57.453141+01:00",
  "UpdatedDate": "2021-01-10T03:44:57.453141+01:00",
  "Description": "Operative background data-warehouse",
  "Postit": "possimus",
  "CreatedBy": null,
  "UpdatedBy": null,
  "Associate": null,
  "ProjectStatus": null,
  "ProjectType": null,
  "HasImage": false,
  "ImageDescription": "Face to face optimizing info-mediaries",
  "ActiveStatusMonitorId": 534,
  "Links": [
    {
      "EntityName": "Aufderhar, Harvey and Leannon",
      "Id": 705,
      "Description": "Integrated dedicated capacity",
      "ExtraInfo": "cumque",
      "LinkId": 940,
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 566
        }
      }
    }
  ],
  "ActiveLinks": 217,
  "Completed": false,
  "NextMilestoneDate": "1998-02-27T03:44:57.453141+01:00",
  "NmdAppointmentId": 222,
  "EndDate": "2013-03-16T03:44:57.453141+01:00",
  "ActiveErpLinks": 407,
  "UserDefinedFields": {
    "SuperOffice:1": "Mrs. Angel Moses Harris II",
    "SuperOffice:2": "Marlen Kessler"
  },
  "ExtraFields": {
    "ExtraFields1": "totam",
    "ExtraFields2": "odit"
  },
  "CustomFields": {
    "CustomFields1": "velit",
    "CustomFields2": "sapiente"
  },
  "PublishEventDate": "2014-09-24T03:44:57.453141+02:00",
  "PublishTo": "2008-07-25T03:44:57.453141+02:00",
  "PublishFrom": "2006-02-16T03:44:57.453141+01:00",
  "IsPublished": true,
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.String",
      "FieldLength": 613
    }
  },
  "_Links": {
    "Self": "https://www.example.com/api/v1/project/321",
    "Archive": "https://www.example.com/api/v1/project"
  }
}
```