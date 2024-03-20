---
title: POST Agents/Person/ChangeCountry
uid: v1PersonAgent_ChangeCountry
generated: true
---

# POST Agents/Person/ChangeCountry

```http
POST /api/v1/Agents/Person/ChangeCountry
```

Change country regenerates the default values and localized information such as phone number and address format for this entity.







## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category". Default = show all fields. |

```http
POST /api/v1/Agents/Person/ChangeCountry?$select=name,department,category/id
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

PersonEntity, ToCountryId 

| Property Name | Type |  Description |
|----------------|------|--------------|
| PersonEntity | PersonEntity |  |
| ToCountryId | Integer |  |

## Response:

OK

| Response | Description |
|----------------|-------------|
| 200 | OK |

### Response body: PersonEntity

| Property Name | Type |  Description |
|----------------|------|--------------|
| PersonId | int32 | Primary key |
| Firstname | string | First name |
| MiddleName | string | Middle name or 'van' etc. |
| Lastname | string | Last name |
| Mrmrs | string | e.g. Mrs   sex_title  Use MDO List name "mrmrs" to get list items. |
| Title | string | Title |
| UpdatedDate | date-time | Last updated date  in UTC. |
| CreatedDate | date-time | Registered date  in UTC. |
| BirthDate | date-time | The Person birth date as UTC Date. Year 1 = Null. Year 2 = unknown year. |
| CreatedBy | Associate | The user that created the person object |
| Emails | array | A collection of the person's emails |
| Description | string | The actual text, max 2047 significant characters even though it is stored as a larger data type on some databases |
| IsAssociate | bool | Checks if the person object is an associate. The property is read-only. |
| PrivatePhones | array | Returns a collection of phone numbers that belong to the contact person. |
| Faxes | array | Returns a collection of fax numbers that belong to the contact person. |
| MobilePhones | array | Returns a collection of mobile phone numbers that belong to the contact person. |
| OfficePhones | array | Returns a collection of office phone numbers that belong to the contact person. |
| OtherPhones | array | Returns a collection of pagers that belong to the contact person. |
| Position | Position | The position. This is a predefined SuperOffice value, different from Title  Use MDO List name "perspos" to get list items. |
| UpdatedBy | Associate | The person that last updated the person object |
| Contact | Contact | The contact the contact person is registered on. This is required unless the 'MandatoryContactOnPerson' preference is set.  Use MDO List name "contact_new" to get list items. |
| Country | Country | The country this contact person is located in.  Use MDO List name "country" to get list items. |
| Interests | array | The person's available and selected interests.  Use MDO List name "persint" to get list items. |
| PersonNumber | string | Alphanumeric user field |
| FullName | string | The person's full name localized to the current culture/country.  (internal name used in clients for employees) |
| NoMailing | bool | Spam filter. Indicates if this person should retrieve advertising. |
| UsePersonAddress | bool | True if the person's address should be used as mailing address, instead of the contact's address. |
| Retired | bool | True if the user is retired and should have no rights, not appear in lists, etc. |
| Urls | array | The urls related to this person. |
| FormalName | string | Get formal name for a person, as used in labels. (Full name + person title + academic title) |
| Address | Address | Structure holding formatted address data. The layout of the array structure indicates the layout of the localized address. |
| Post3 | string | Postal address, used in Japanese versions only |
| Post2 | string | Postal address, used in Japanese versions only |
| Post1 | string | Postal address, used in Japanese versions only |
| Kanalname | string | Kana last name, used in Japanese versions only |
| Kanafname | string | Kana first name, used in Japanese versions only |
| CorrespondingAssociate | Associate | The associate corresponding to this person. Will be empty if the person is not a user (internal associate user, external user). |
| Category | Category | Person's category. Usually null. Refer to the Contact.Category instead.  Intended for use when individual persons are created. (i.e. when Person.Contact is blank)  Use MDO List name "category" to get list items. |
| Business | Business | Person's business - usually blank. Use Contact.Business instead. Intended for use when individual persons are created. (i.e. when Person.Contact is blank)  Use MDO List name "business" to get list items. |
| Associate | Associate | The associate owning this person (similar to contact.Associate) - usually blank. Use the Person.Contact.Associate instead.  Intended for use when individual persons are created (i.e. when Person.Contact is blank)  Use MDO List name "associate" to get list items. |
| Salutation | string | Academic title, populated from Salutation list but can be overwritten with anything at all  Use MDO List name "salutation" to get list items. |
| ActiveInterests | int32 | The number of active interests. |
| SupportAssociate | Associate | Use MDO List name "associate" to get list items. |
| TicketPriority | TicketPriority | Use MDO List name "ticketpriority" to get list items. |
| CustomerLanguage | CustomerLanguage | Use MDO List name "customerlanguage" to get list items. |
| DbiAgentId | int32 | Integration agent (eJournal) |
| DbiKey | string | The primary key for the integrated entry in the external datasource. |
| DbiLastModified | date-time | When the entry was last modified. |
| DbiLastSyncronized | date-time | Last external syncronization. |
| SentInfo | int32 | Has information on username/password been sent (ejournal) |
| ShowContactTickets | int32 | Should tickets related to the company be shown to this person |
| UserInfo | UserInfo | Information about the user if this person is a user.  If IsAssociate (e.g. is user is true) the UserInfo will be provided. |
| ChatEmails | array |  |
| InternetPhones | array |  |
| Source | int32 | How did we get this person? For future integration needs |
| ActiveErpLinks | int32 | How many active ERP links are there for this person? |
| ShipmentTypes | array | The person's available and selected shipment types. |
| Consents | array | The person's available consent information. Missing consents are not deleted. To remove a consent, mark its legalbase as 'WITHDRAWN' |
| BounceEmails | array | Email addresses with a positive bounce counter. |
| ActiveStatusMonitorId | int32 | Active status monitor identity with the lowest rank for person |
| UserDefinedFields | object | Deprecated: Use {SuperOffice.CRM.Services.PersonEntity.CustomFields} instead. Dictionary of user defined field data. The key string is the ProgId of the UdefField, or if the ProgId is empty it is a string of the format "SuperOffice:[UdefFieldIdentity]", e.g. "SuperOffice:1234" |
| ExtraFields | object | Deprecated: Use {SuperOffice.CRM.Services.PersonEntity.CustomFields} instead. Extra fields added to the carrier. This could be data from Plug-ins, the foreign key system, external applications, etc. |
| CustomFields | object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.PersonEntity.ExtraFields} and UserDefinedFields properties are deprecated in favor of this combined collection. |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |

## Sample request

```http!
POST /api/v1/Agents/Person/ChangeCountry
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: en
Content-Type: application/json; charset=utf-8

{
  "PersonEntity": null,
  "ToCountryId": 408
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "PersonId": 286,
  "Firstname": "Isaiah",
  "MiddleName": "Graham, Hettinger and Gerhold",
  "Lastname": "Yundt",
  "Mrmrs": "error",
  "Title": "sit",
  "UpdatedDate": "1999-02-03T12:19:45.6952931+01:00",
  "CreatedDate": "2015-03-05T12:19:45.6952931+01:00",
  "BirthDate": "2012-11-27T12:19:45.6952931+01:00",
  "CreatedBy": null,
  "Emails": [
    {
      "Value": "qui",
      "StrippedValue": "ipsa",
      "Description": "Reverse-engineered 6th generation data-warehouse",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 50
        }
      }
    },
    {
      "Value": "qui",
      "StrippedValue": "ipsa",
      "Description": "Reverse-engineered 6th generation data-warehouse",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 50
        }
      }
    }
  ],
  "Description": "Public-key 6th generation hierarchy",
  "IsAssociate": true,
  "PrivatePhones": [
    {
      "Value": "nulla",
      "StrippedValue": "sed",
      "Description": "Decentralized contextually-based knowledge base",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 55
        }
      }
    },
    {
      "Value": "nulla",
      "StrippedValue": "sed",
      "Description": "Decentralized contextually-based knowledge base",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 55
        }
      }
    }
  ],
  "Faxes": [
    {
      "Value": "in",
      "StrippedValue": "dolore",
      "Description": "Monitored motivating task-force",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 94
        }
      }
    },
    {
      "Value": "in",
      "StrippedValue": "dolore",
      "Description": "Monitored motivating task-force",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 94
        }
      }
    }
  ],
  "MobilePhones": [
    {
      "Value": "porro",
      "StrippedValue": "maxime",
      "Description": "Configurable 3rd generation artificial intelligence",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 639
        }
      }
    },
    {
      "Value": "porro",
      "StrippedValue": "maxime",
      "Description": "Configurable 3rd generation artificial intelligence",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 639
        }
      }
    }
  ],
  "OfficePhones": [
    {
      "Value": "distinctio",
      "StrippedValue": "laudantium",
      "Description": "Automated bifurcated forecast",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 118
        }
      }
    },
    {
      "Value": "distinctio",
      "StrippedValue": "laudantium",
      "Description": "Automated bifurcated forecast",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 118
        }
      }
    }
  ],
  "OtherPhones": [
    {
      "Value": "ipsum",
      "StrippedValue": "porro",
      "Description": "Compatible 24/7 function",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 746
        }
      }
    },
    {
      "Value": "ipsum",
      "StrippedValue": "porro",
      "Description": "Compatible 24/7 function",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 746
        }
      }
    }
  ],
  "Position": null,
  "UpdatedBy": null,
  "Contact": null,
  "Country": null,
  "Interests": [
    {
      "Id": 813,
      "Name": "Pfannerstill LLC",
      "ToolTip": "Cum reiciendis.",
      "Deleted": false,
      "Rank": 879,
      "Type": "nihil",
      "ColorBlock": 594,
      "IconHint": "omnis",
      "Selected": false,
      "LastChanged": "2005-06-21T12:19:45.6952931+02:00",
      "ChildItems": [
        {},
        {}
      ],
      "ExtraInfo": "rerum",
      "StyleHint": "maxime",
      "Hidden": true,
      "FullName": "Dr. Wilhelm Morar",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 653
        }
      }
    }
  ],
  "PersonNumber": "1321629",
  "FullName": "Kirsten Herbert Watsica V",
  "NoMailing": false,
  "UsePersonAddress": true,
  "Retired": false,
  "Urls": [
    {
      "Value": "quo",
      "StrippedValue": "accusamus",
      "Description": "Distributed systematic extranet",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 148
        }
      }
    },
    {
      "Value": "quo",
      "StrippedValue": "accusamus",
      "Description": "Distributed systematic extranet",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 148
        }
      }
    }
  ],
  "FormalName": "Goldner Group",
  "Address": null,
  "Post3": "cum",
  "Post2": "et",
  "Post1": "repellendus",
  "Kanalname": "impedit",
  "Kanafname": "voluptatem",
  "CorrespondingAssociate": null,
  "Category": null,
  "Business": null,
  "Associate": null,
  "Salutation": "quos",
  "ActiveInterests": 292,
  "SupportAssociate": null,
  "TicketPriority": null,
  "CustomerLanguage": null,
  "DbiAgentId": 796,
  "DbiKey": "ut",
  "DbiLastModified": "2022-12-05T12:19:45.6952931+01:00",
  "DbiLastSyncronized": "2000-08-12T12:19:45.6952931+02:00",
  "SentInfo": 115,
  "ShowContactTickets": 863,
  "UserInfo": null,
  "ChatEmails": [
    {
      "Value": "dicta",
      "StrippedValue": "omnis",
      "Description": "Right-sized web-enabled knowledge base",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 410
        }
      }
    },
    {
      "Value": "dicta",
      "StrippedValue": "omnis",
      "Description": "Right-sized web-enabled knowledge base",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 410
        }
      }
    }
  ],
  "InternetPhones": [
    {
      "Value": "sed",
      "StrippedValue": "temporibus",
      "Description": "Secured regional artificial intelligence",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 647
        }
      }
    },
    {
      "Value": "sed",
      "StrippedValue": "temporibus",
      "Description": "Secured regional artificial intelligence",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 647
        }
      }
    }
  ],
  "Source": 493,
  "ActiveErpLinks": 634,
  "ShipmentTypes": [
    {
      "Id": 658,
      "Name": "Stracke-Ruecker",
      "ToolTip": "Dolores cupiditate.",
      "Deleted": false,
      "Rank": 545,
      "Type": "asperiores",
      "ColorBlock": 468,
      "IconHint": "culpa",
      "Selected": false,
      "LastChanged": "2003-09-06T12:19:45.6952931+02:00",
      "ChildItems": [
        {},
        {}
      ],
      "ExtraInfo": "nihil",
      "StyleHint": "consequatur",
      "Hidden": true,
      "FullName": "Jane Kuhlman",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 101
        }
      }
    }
  ],
  "Consents": [
    {
      "ConsentPersonId": 888,
      "Comment": "autem",
      "Registered": "2016-12-15T12:19:45.6952931+01:00",
      "RegisteredAssociateId": 413,
      "Updated": "1998-10-14T12:19:45.6952931+02:00",
      "UpdatedAssociateId": 471,
      "LegalBaseId": 367,
      "LegalBaseKey": "non",
      "LegalBaseName": "Torp Group",
      "ConsentPurposeId": 741,
      "ConsentPurposeKey": "nostrum",
      "ConsentPurposeName": "Beatty, Shanahan and Herzog",
      "ConsentSourceId": 448,
      "ConsentSourceKey": "ut",
      "ConsentSourceName": "Leffler-Schumm",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 436
        }
      }
    }
  ],
  "BounceEmails": [
    "wyman_keeling@runte.com",
    "devon_waelchi@rutherfordlebsack.com"
  ],
  "ActiveStatusMonitorId": 251,
  "UserDefinedFields": {
    "SuperOffice:1": "Dr. Edwardo Ernie Hansen Sr.",
    "SuperOffice:2": "Candace Bahringer"
  },
  "ExtraFields": {
    "ExtraFields1": "et",
    "ExtraFields2": "accusamus"
  },
  "CustomFields": {
    "CustomFields1": "sit",
    "CustomFields2": "consequatur"
  },
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.String",
      "FieldLength": 469
    }
  }
}
```