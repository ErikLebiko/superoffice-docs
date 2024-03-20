---
title: GET Contact/default
uid: v1ContactEntity_DefaultContactEntity
generated: true
---

# GET Contact/default

```http
GET /api/v1/Contact/default
```

Set default values into a new ContactEntity.


NetServer calculates default values on the entity, which is required when creating/storing a new instance Calls the Contact agent service CreateDefaultContactEntity.







## Request Headers

| Parameter Name | Description |
|----------------|-------------|
| Authorization  | Supports 'Basic', 'SoTicket' and 'Bearer' schemes, depending on installation type. |
| X-XSRF-TOKEN   | If not using Authorization header, you must provide XSRF value from cookie or hidden input field |
| Accept         | Content-type(s) you would like the response in: `application/json`, `text/json`, `application/xml`, `text/xml`, `application/json-patch+json`, `application/merge-patch+json` |
| Accept-Language | Convert string references and multi-language values into a specified language (iso2) code. |
| SO-Language | Convert string references and multi-language values into a specified language (iso2) code. Overrides Accept-Language value. |
| SO-Culture | Number, date formatting in a specified culture (iso2 language) code. Partially overrides SO-Language/Accept-Language value. Ignored if no Language set. |
| SO-TimeZone | Specify the timezone code that you would like date/time responses converted to. |
| SO-AppToken | The application token that identifies the partner app. Used when calling Online WebAPI from a server. |


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
GET /api/v1/Contact/default
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: *
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Last-Modified: Wed, 14 Sep 2005 12:19:53 G9T

{
  "ContactId": 798,
  "Name": "Blick, Stokes and Medhurst",
  "Department": "",
  "OrgNr": "814671",
  "Number1": "647659",
  "Number2": "866856",
  "UpdatedDate": "2005-09-14T12:19:53.1962056+02:00",
  "CreatedDate": "2023-06-03T12:19:53.1962056+02:00",
  "Emails": [
    {
      "Value": "recusandae",
      "StrippedValue": "ea",
      "Description": "Cross-group zero administration local area network",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 56
        }
      }
    },
    {
      "Value": "recusandae",
      "StrippedValue": "ea",
      "Description": "Cross-group zero administration local area network",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 56
        }
      }
    }
  ],
  "Interests": [
    {
      "Id": 777,
      "Name": "DuBuque Inc and Sons",
      "ToolTip": "Ducimus veritatis itaque eum rerum deleniti.",
      "Deleted": true,
      "Rank": 420,
      "Type": "necessitatibus",
      "ColorBlock": 907,
      "IconHint": "odit",
      "Selected": false,
      "LastChanged": "2021-08-14T12:19:53.1962056+02:00",
      "ChildItems": [
        {},
        {}
      ],
      "ExtraInfo": "esse",
      "StyleHint": "recusandae",
      "Hidden": false,
      "FullName": "Brennon Witting",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 909
        }
      }
    }
  ],
  "Urls": [
    {
      "Value": "ut",
      "StrippedValue": "voluptate",
      "Description": "Fundamental dedicated capability",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 720
        }
      }
    },
    {
      "Value": "ut",
      "StrippedValue": "voluptate",
      "Description": "Fundamental dedicated capability",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 720
        }
      }
    }
  ],
  "Phones": [
    {
      "Value": "ad",
      "StrippedValue": "voluptate",
      "Description": "Proactive bandwidth-monitored monitoring",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 586
        }
      }
    },
    {
      "Value": "ad",
      "StrippedValue": "voluptate",
      "Description": "Proactive bandwidth-monitored monitoring",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 586
        }
      }
    }
  ],
  "Faxes": [
    {
      "Value": "quam",
      "StrippedValue": "quia",
      "Description": "Decentralized empowering knowledge user",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 2
        }
      }
    },
    {
      "Value": "quam",
      "StrippedValue": "quia",
      "Description": "Decentralized empowering knowledge user",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 2
        }
      }
    }
  ],
  "Description": "Streamlined fresh-thinking moderator",
  "UpdatedBy": null,
  "CreatedBy": null,
  "Associate": null,
  "Business": null,
  "Category": null,
  "Country": null,
  "Persons": [
    {
      "Position": "et",
      "PersonId": 774,
      "Mrmrs": "possimus",
      "Firstname": "Allan",
      "Lastname": "Blanda",
      "MiddleName": "Ruecker, Torphy and Schamberger",
      "Title": "praesentium",
      "Description": "Managed needs-based neural-net",
      "Email": "carolanne_gleason@jewess.uk",
      "FullName": "Alana Murphy",
      "DirectPhone": "1-247-475-4485 x265",
      "FormalName": "Tremblay-Kihn",
      "CountryId": 902,
      "ContactId": 574,
      "ContactName": "Purdy, Gislason and Turner",
      "Retired": 799,
      "Rank": 591,
      "ActiveInterests": 754,
      "ContactDepartment": "",
      "ContactCountryId": 721,
      "ContactOrgNr": "1503691",
      "FaxPhone": "(920)937-5187",
      "MobilePhone": "(325)168-3434 x8911",
      "ContactPhone": "986.262.4344",
      "AssociateName": "Ankunding, Littel and Simonis",
      "AssociateId": 827,
      "UsePersonAddress": false,
      "ContactFax": "tempora",
      "Kanafname": "exercitationem",
      "Kanalname": "sequi",
      "Post1": "id",
      "Post2": "inventore",
      "Post3": "blanditiis",
      "EmailName": "margarita@wittingberge.us",
      "ContactFullName": "Mr. Mason Sauer",
      "ActiveErpLinks": 523,
      "TicketPriorityId": 564,
      "SupportLanguageId": 316,
      "SupportAssociateId": 369,
      "CategoryName": "VIP Customer",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 359
        }
      }
    }
  ],
  "NoMailing": false,
  "Kananame": "sint",
  "Xstop": true,
  "ActiveInterests": 661,
  "GroupId": 246,
  "ActiveStatusMonitorId": 500,
  "SupportAssociate": null,
  "TicketPriority": null,
  "CustomerLanguage": null,
  "Deleted": 150,
  "DbiAgentId": 11,
  "DbiLastSyncronized": "2017-08-03T12:19:53.1962056+02:00",
  "DbiKey": "incidunt",
  "DbiLastModified": "2015-07-19T12:19:53.1962056+02:00",
  "SupportPerson": null,
  "Address": null,
  "Source": 704,
  "ActiveErpLinks": 125,
  "BounceEmails": [
    "stanton_huel@thompsonmarquardt.com",
    "chandler@oreillyconn.ca"
  ],
  "Domains": [
    "ea",
    "distinctio"
  ],
  "UserDefinedFields": {
    "SuperOffice:1": "Prof. Lester Brekke",
    "SuperOffice:2": "789544441"
  },
  "ExtraFields": {
    "ExtraFields1": "hic",
    "ExtraFields2": "expedita"
  },
  "CustomFields": {
    "CustomFields1": "vero",
    "CustomFields2": "magni"
  },
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 773
    }
  }
}
```