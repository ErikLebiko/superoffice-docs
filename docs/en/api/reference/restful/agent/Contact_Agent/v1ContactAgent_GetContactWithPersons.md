---
title: POST Agents/Contact/GetContactWithPersons
uid: v1ContactAgent_GetContactWithPersons
generated: true
---

# POST Agents/Contact/GetContactWithPersons

```http
POST /api/v1/Agents/Contact/GetContactWithPersons
```

Returns the contact with all the contact persons belonging to the contact







## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category". Default = show all fields. |

```http
POST /api/v1/Agents/Contact/GetContactWithPersons?$select=name,department,category/id
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

## Request Body: request 

ContactId 

| Property Name | Type |  Description |
|----------------|------|--------------|
| ContactId | Integer |  |

## Response:

OK

| Response | Description |
|----------------|-------------|
| 200 | OK |

### Response body: ContactEntity

| Property Name | Type |  Description |
|----------------|------|--------------|
| ContactId | int32 | Primary key |
| Name | string | Contact name |
| Department | string | Department |
| OrgNr | string | VAT number or similar |
| Number1 | string | Alphanumeric user field |
| Number2 | string | Alphanumeric user field |
| UpdatedDate | date-time | Date last updated  in UTC. |
| CreatedDate | date-time | Date registered  in UTC. |
| Emails | array | The contact's email |
| Interests | array | The contact's available and selected interests.  Use MDO List name "contint" to get list items. |
| Urls | array | The contact's internet adresses |
| Phones | array | The contact's phone numbers |
| Faxes | array | The contact's fax numbers |
| Description | string | Description of the contact. Usually shown as a postit note. |
| UpdatedBy | Associate | The user that last updated the contact |
| CreatedBy | Associate | The user that created the contact |
| Associate | Associate | The user that owns this contact.  Use MDO List name "associate" to get list items. |
| Business | Business | The business that the contact is associated with. The GUI forces the user to enter a business type.  Use MDO List name "business" to get list items. |
| Category | Category | The category that is set on the company. The GUI forces the user to enter a category type  Use MDO List name "category" to get list items. |
| Country | Country | The country this contact is located in. The country a contact is saved with, affects the phone number format, and the address layout.  Use MDO List name "country" to get list items. |
| Persons | array | The persons belonging to the contact. |
| NoMailing | bool | Spam filter. Indicates if this contact should retrieve advertising. |
| Kananame | string | Contact kana name, used in Japanese versions only |
| Xstop | bool | STOP flag |
| ActiveInterests | int32 | The number of active interests. |
| GroupId | int32 | Group id of original owning associate, semantics like appnt.grp_id |
| ActiveStatusMonitorId | int32 | Active status monitor identity with the lowest rank for contact |
| SupportAssociate | Associate | Use MDO List name "associate" to get list items. |
| TicketPriority | TicketPriority | Use MDO List name "ticketpriority" to get list items. |
| CustomerLanguage | CustomerLanguage | customerlanguage |
| Deleted | int32 | If nonzero, then this contact is 'deleted' and should generally not be shown |
| DbiAgentId | int32 | Integration agent (eJournal) |
| DbiLastSyncronized | date-time | Last external syncronization. |
| DbiKey | string | The primary key for the integrated entry in the external datasource. |
| DbiLastModified | date-time | When the entry was last modified. |
| SupportPerson | Person | Carrier object for Person. Services for the Person Carrier is available from the Person Agent. |
| Address | Address | Street and/or Postal address, in both formatted and structured forms. You only need to modify one of the two for the change to be registered.  Carrier object for Address. |
| Source | int32 | How did we get this contact? For future integration needs |
| ActiveErpLinks | int32 | The number of active erp links |
| BounceEmails | array | Email addresses with a positive bounce counter. |
| Domains | array | Web domains for this contact, ordered in array by rank |
| UserDefinedFields | object | Deprecated: Use {SuperOffice.CRM.Services.ContactEntity.CustomFields} instead. Dictionary of user defined field data. The key string is the ProgId of the UdefField, or if the ProgId is empty it is a string of the format "SuperOffice:[UdefFieldIdentity]", e.g. "SuperOffice:1234" |
| ExtraFields | object | Deprecated: Use {SuperOffice.CRM.Services.ContactEntity.CustomFields} instead. Extra fields added to the carrier. This could be data from Plug-ins, the foreign key system, external applications, etc. |
| CustomFields | object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.ContactEntity.ExtraFields} and UserDefinedFields properties are deprecated in favor of this combined collection. |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |

## Sample request

```http!
POST /api/v1/Agents/Contact/GetContactWithPersons
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: en
Content-Type: application/json; charset=utf-8

{
  "ContactId": 504
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "ContactId": 254,
  "Name": "Cruickshank Inc and Sons",
  "Department": "",
  "OrgNr": "1826258",
  "Number1": "638924",
  "Number2": "927611",
  "UpdatedDate": "2003-04-19T10:30:23.3199404+02:00",
  "CreatedDate": "2011-04-29T10:30:23.3199404+02:00",
  "Emails": [
    {
      "Value": "consequatur",
      "StrippedValue": "rem",
      "Description": "Cross-platform modular data-warehouse",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 925
        }
      }
    },
    {
      "Value": "consequatur",
      "StrippedValue": "rem",
      "Description": "Cross-platform modular data-warehouse",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 925
        }
      }
    }
  ],
  "Interests": [
    {
      "Id": 265,
      "Name": "Cartwright Inc and Sons",
      "ToolTip": "Facere aut nesciunt at.",
      "Deleted": false,
      "Rank": 759,
      "Type": "quia",
      "ColorBlock": 129,
      "IconHint": "voluptas",
      "Selected": true,
      "LastChanged": "2007-02-03T10:30:23.3199404+01:00",
      "ChildItems": [
        {},
        {}
      ],
      "ExtraInfo": "qui",
      "StyleHint": "qui",
      "Hidden": false,
      "FullName": "Mrs. Miguel Wilderman",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 541
        }
      }
    }
  ],
  "Urls": [
    {
      "Value": "temporibus",
      "StrippedValue": "est",
      "Description": "Adaptive needs-based infrastructure",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 162
        }
      }
    },
    {
      "Value": "temporibus",
      "StrippedValue": "est",
      "Description": "Adaptive needs-based infrastructure",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 162
        }
      }
    }
  ],
  "Phones": [
    {
      "Value": "eligendi",
      "StrippedValue": "sed",
      "Description": "Persistent asynchronous orchestration",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 300
        }
      }
    },
    {
      "Value": "eligendi",
      "StrippedValue": "sed",
      "Description": "Persistent asynchronous orchestration",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 300
        }
      }
    }
  ],
  "Faxes": [
    {
      "Value": "earum",
      "StrippedValue": "nostrum",
      "Description": "Proactive contextually-based website",
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
      "Value": "earum",
      "StrippedValue": "nostrum",
      "Description": "Proactive contextually-based website",
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
  "Description": "Integrated optimizing encryption",
  "UpdatedBy": null,
  "CreatedBy": null,
  "Associate": null,
  "Business": null,
  "Category": null,
  "Country": null,
  "Persons": [
    {
      "Position": "perspiciatis",
      "PersonId": 966,
      "Mrmrs": "sed",
      "Firstname": "Justina",
      "Lastname": "Kirlin",
      "MiddleName": "Hilpert-Watsica",
      "Title": "earum",
      "Description": "Seamless static circuit",
      "Email": "reid.reinger@rippin.uk",
      "FullName": "Miss Ernestina Klocko",
      "DirectPhone": "875-551-8694 x332",
      "FormalName": "Rath-Pagac",
      "CountryId": 883,
      "ContactId": 968,
      "ContactName": "Kihn, Watsica and Kovacek",
      "Retired": 692,
      "Rank": 707,
      "ActiveInterests": 672,
      "ContactDepartment": "",
      "ContactCountryId": 487,
      "ContactOrgNr": "1693201",
      "FaxPhone": "160.155.4643 x500",
      "MobilePhone": "1-627-027-2064 x263",
      "ContactPhone": "1-625-893-4668",
      "AssociateName": "Jacobi, McLaughlin and Cummerata",
      "AssociateId": 521,
      "UsePersonAddress": false,
      "ContactFax": "ipsam",
      "Kanafname": "quis",
      "Kanalname": "aut",
      "Post1": "illum",
      "Post2": "magnam",
      "Post3": "omnis",
      "EmailName": "mertie@heidenreich.biz",
      "ContactFullName": "Lamar Beatty",
      "ActiveErpLinks": 26,
      "TicketPriorityId": 849,
      "SupportLanguageId": 691,
      "SupportAssociateId": 27,
      "CategoryName": "VIP Customer",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 531
        }
      }
    }
  ],
  "NoMailing": false,
  "Kananame": "impedit",
  "Xstop": false,
  "ActiveInterests": 763,
  "GroupId": 918,
  "ActiveStatusMonitorId": 208,
  "SupportAssociate": null,
  "TicketPriority": null,
  "CustomerLanguage": null,
  "Deleted": 363,
  "DbiAgentId": 168,
  "DbiLastSyncronized": "2006-06-03T10:30:23.3199404+02:00",
  "DbiKey": "itaque",
  "DbiLastModified": "2019-06-12T10:30:23.3199404+02:00",
  "SupportPerson": null,
  "Address": null,
  "Source": 500,
  "ActiveErpLinks": 804,
  "BounceEmails": [
    "christelle.wiza@harriswunsch.ca",
    "conor@murphy.com"
  ],
  "Domains": [
    "facere",
    "ducimus"
  ],
  "UserDefinedFields": {
    "SuperOffice:1": "True",
    "SuperOffice:2": "1547939132"
  },
  "ExtraFields": {
    "ExtraFields1": "consequatur",
    "ExtraFields2": "eum"
  },
  "CustomFields": {
    "CustomFields1": "possimus",
    "CustomFields2": "dolor"
  },
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.String",
      "FieldLength": 97
    }
  }
}
```