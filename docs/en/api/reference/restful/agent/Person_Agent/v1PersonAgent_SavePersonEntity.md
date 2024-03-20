---
title: POST Agents/Person/SavePersonEntity
uid: v1PersonAgent_SavePersonEntity
generated: true
---

# POST Agents/Person/SavePersonEntity

```http
POST /api/v1/Agents/Person/SavePersonEntity
```

Updates the existing PersonEntity or creates a new PersonEntity if the id parameter is empty








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

The PersonEntity to be saved. 

| Property Name | Type |  Description |
|----------------|------|--------------|
| PersonId | Integer | Primary key |
| Firstname | String | First name |
| MiddleName | String | Middle name or 'van' etc. |
| Lastname | String | Last name |
| Mrmrs | String | e.g. Mrs   sex_title  <para>Use MDO List name "mrmrs" to get list items.</para> |
| Title | String | Title |
| UpdatedDate | String | Last updated date  in UTC. |
| CreatedDate | String | Registered date  in UTC. |
| BirthDate | String | The Person birth date as UTC Date. Year 1 = Null. Year 2 = unknown year. |
| CreatedBy | Associate | The user that created the person object |
| Emails | Array | A collection of the person's emails |
| Description | String | The actual text, max 2047 significant characters even though it is stored as a larger data type on some databases |
| IsAssociate | Boolean | Checks if the person object is an associate. The property is read-only. |
| PrivatePhones | Array | Returns a collection of phone numbers that belong to the contact person. |
| Faxes | Array | Returns a collection of fax numbers that belong to the contact person. |
| MobilePhones | Array | Returns a collection of mobile phone numbers that belong to the contact person. |
| OfficePhones | Array | Returns a collection of office phone numbers that belong to the contact person. |
| OtherPhones | Array | Returns a collection of pagers that belong to the contact person. |
| Position | Position | The position. This is a predefined SuperOffice value, different from Title  <para>Use MDO List name "perspos" to get list items.</para> |
| UpdatedBy | Associate | The person that last updated the person object |
| Contact | Contact | The contact the contact person is registered on. This is required unless the 'MandatoryContactOnPerson' preference is set.  <para>Use MDO List name "contact_new" to get list items.</para> |
| Country | Country | The country this contact person is located in.  <para>Use MDO List name "country" to get list items.</para> |
| Interests | Array | The person's available and selected interests.  <para>Use MDO List name "persint" to get list items.</para> |
| PersonNumber | String | Alphanumeric user field |
| FullName | String | The person's full name localized to the current culture/country.  (internal name used in clients for employees) |
| NoMailing | Boolean | Spam filter. Indicates if this person should retrieve advertising. |
| UsePersonAddress | Boolean | True if the person's address should be used as mailing address, instead of the contact's address. |
| Retired | Boolean | True if the user is retired and should have no rights, not appear in lists, etc. |
| Urls | Array | The urls related to this person. |
| FormalName | String | Get formal name for a person, as used in labels. (Full name + person title + academic title) |
| Address | Address | Structure holding formatted address data. The layout of the array structure indicates the layout of the localized address. |
| Post3 | String | Postal address, used in Japanese versions only |
| Post2 | String | Postal address, used in Japanese versions only |
| Post1 | String | Postal address, used in Japanese versions only |
| Kanalname | String | Kana last name, used in Japanese versions only |
| Kanafname | String | Kana first name, used in Japanese versions only |
| CorrespondingAssociate | Associate | The associate corresponding to this person. Will be empty if the person is not a user (internal associate user, external user). |
| Category | Category | Person's category. Usually null. Refer to the Contact.Category instead.  Intended for use when individual persons are created. (i.e. when Person.Contact is blank)  <para>Use MDO List name "category" to get list items.</para> |
| Business | Business | Person's business - usually blank. Use Contact.Business instead. Intended for use when individual persons are created. (i.e. when Person.Contact is blank)  <para>Use MDO List name "business" to get list items.</para> |
| Associate | Associate | The associate owning this person (similar to contact.Associate) - usually blank. Use the Person.Contact.Associate instead.  Intended for use when individual persons are created (i.e. when Person.Contact is blank)  <para>Use MDO List name "associate" to get list items.</para> |
| Salutation | String | Academic title, populated from Salutation list but can be overwritten with anything at all  <para>Use MDO List name "salutation" to get list items.</para> |
| ActiveInterests | Integer | The number of active interests. |
| SupportAssociate | Associate | <para>Use MDO List name "associate" to get list items.</para> |
| TicketPriority | TicketPriority | <para>Use MDO List name "ticketpriority" to get list items.</para> |
| CustomerLanguage | CustomerLanguage | <para>Use MDO List name "customerlanguage" to get list items.</para> |
| DbiAgentId | Integer | Integration agent (eJournal) |
| DbiKey | String | The primary key for the integrated entry in the external datasource. |
| DbiLastModified | String | When the entry was last modified. |
| DbiLastSyncronized | String | Last external syncronization. |
| SentInfo | Integer | Has information on username/password been sent (ejournal) |
| ShowContactTickets | Integer | Should tickets related to the company be shown to this person |
| UserInfo | UserInfo | Information about the user if this person is a user.  If IsAssociate (e.g. is user is true) the UserInfo will be provided. |
| ChatEmails | Array |  |
| InternetPhones | Array |  |
| Source | Integer | How did we get this person? For future integration needs |
| ActiveErpLinks | Integer | How many active ERP links are there for this person? |
| ShipmentTypes | Array | The person's available and selected shipment types. |
| Consents | Array | The person's available consent information. Missing consents are not deleted. To remove a consent, mark its legalbase as 'WITHDRAWN' |
| BounceEmails | Array | Email addresses with a positive bounce counter. |
| ActiveStatusMonitorId | Integer | Active status monitor identity with the lowest rank for person |
| UserDefinedFields | Object | Deprecated: Use {SuperOffice.CRM.Services.PersonEntity.CustomFields} instead. Dictionary of user defined field data. The key string is the ProgId of the UdefField, or if the ProgId is empty it is a string of the format "SuperOffice:[UdefFieldIdentity]", e.g. "SuperOffice:1234" |
| ExtraFields | Object | Deprecated: Use {SuperOffice.CRM.Services.PersonEntity.CustomFields} instead. Extra fields added to the carrier. This could be data from Plug-ins, the foreign key system, external applications, etc. |
| CustomFields | Object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.PersonEntity.ExtraFields} and <see cref="P:SuperOffice.CRM.Services.PersonEntity.UserDefinedFields">UserDefinedFields</see> properties are deprecated in favor of this combined collection. |

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
POST /api/v1/Agents/Person/SavePersonEntity
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: en
Content-Type: application/json; charset=utf-8

{
  "PersonId": 633,
  "Firstname": "Demario",
  "MiddleName": "Sanford, Becker and Rau",
  "Lastname": "Glover",
  "Mrmrs": "provident",
  "Title": "accusantium",
  "UpdatedDate": "2021-06-18T12:19:45.617185+02:00",
  "CreatedDate": "2022-02-26T12:19:45.617185+01:00",
  "BirthDate": "1997-03-02T12:19:45.617185+01:00",
  "CreatedBy": null,
  "Emails": [
    {
      "Value": "et",
      "StrippedValue": "assumenda",
      "Description": "Vision-oriented high-level flexibility"
    },
    {
      "Value": "et",
      "StrippedValue": "assumenda",
      "Description": "Vision-oriented high-level flexibility"
    }
  ],
  "Description": "Mandatory coherent complexity",
  "IsAssociate": true,
  "PrivatePhones": [
    {
      "Value": "veritatis",
      "StrippedValue": "est",
      "Description": "Centralized real-time approach"
    },
    {
      "Value": "veritatis",
      "StrippedValue": "est",
      "Description": "Centralized real-time approach"
    }
  ],
  "Faxes": [
    {
      "Value": "doloribus",
      "StrippedValue": "non",
      "Description": "Operative hybrid array"
    },
    {
      "Value": "doloribus",
      "StrippedValue": "non",
      "Description": "Operative hybrid array"
    }
  ],
  "MobilePhones": [
    {
      "Value": "repellat",
      "StrippedValue": "nobis",
      "Description": "Multi-layered bifurcated matrices"
    },
    {
      "Value": "repellat",
      "StrippedValue": "nobis",
      "Description": "Multi-layered bifurcated matrices"
    }
  ],
  "OfficePhones": [
    {
      "Value": "rerum",
      "StrippedValue": "officiis",
      "Description": "Triple-buffered impactful website"
    },
    {
      "Value": "rerum",
      "StrippedValue": "officiis",
      "Description": "Triple-buffered impactful website"
    }
  ],
  "OtherPhones": [
    {
      "Value": "tempore",
      "StrippedValue": "soluta",
      "Description": "Extended system-worthy open architecture"
    },
    {
      "Value": "tempore",
      "StrippedValue": "soluta",
      "Description": "Extended system-worthy open architecture"
    }
  ],
  "Position": null,
  "UpdatedBy": null,
  "Contact": null,
  "Country": null,
  "Interests": [
    {
      "Id": 843,
      "Name": "Medhurst Group",
      "ToolTip": "Harum soluta sit repudiandae.",
      "Deleted": false,
      "Rank": 410,
      "Type": "unde",
      "ColorBlock": 246,
      "IconHint": "perferendis",
      "Selected": false,
      "LastChanged": "1998-09-06T12:19:45.6328079+02:00",
      "ChildItems": [
        {},
        {}
      ],
      "ExtraInfo": "est",
      "StyleHint": "modi",
      "Hidden": true,
      "FullName": "Moshe Powlowski"
    }
  ],
  "PersonNumber": "1183297",
  "FullName": "Dr. Lela Witting I",
  "NoMailing": false,
  "UsePersonAddress": false,
  "Retired": false,
  "Urls": [
    {
      "Value": "ut",
      "StrippedValue": "debitis",
      "Description": "Multi-lateral multimedia internet solution"
    },
    {
      "Value": "ut",
      "StrippedValue": "debitis",
      "Description": "Multi-lateral multimedia internet solution"
    }
  ],
  "FormalName": "DuBuque-Boehm",
  "Address": null,
  "Post3": "omnis",
  "Post2": "minus",
  "Post1": "quaerat",
  "Kanalname": "ducimus",
  "Kanafname": "vero",
  "CorrespondingAssociate": null,
  "Category": null,
  "Business": null,
  "Associate": null,
  "Salutation": "enim",
  "ActiveInterests": 432,
  "SupportAssociate": null,
  "TicketPriority": null,
  "CustomerLanguage": null,
  "DbiAgentId": 159,
  "DbiKey": "rem",
  "DbiLastModified": "2010-12-05T12:19:45.6328079+01:00",
  "DbiLastSyncronized": "2016-04-24T12:19:45.6328079+02:00",
  "SentInfo": 38,
  "ShowContactTickets": 240,
  "UserInfo": null,
  "ChatEmails": [
    {
      "Value": "eos",
      "StrippedValue": "placeat",
      "Description": "Upgradable stable infrastructure"
    },
    {
      "Value": "eos",
      "StrippedValue": "placeat",
      "Description": "Upgradable stable infrastructure"
    }
  ],
  "InternetPhones": [
    {
      "Value": "quae",
      "StrippedValue": "qui",
      "Description": "Cross-group neutral contingency"
    },
    {
      "Value": "quae",
      "StrippedValue": "qui",
      "Description": "Cross-group neutral contingency"
    }
  ],
  "Source": 861,
  "ActiveErpLinks": 404,
  "ShipmentTypes": [
    {
      "Id": 255,
      "Name": "Mills Inc and Sons",
      "ToolTip": "Optio aut.",
      "Deleted": true,
      "Rank": 314,
      "Type": "commodi",
      "ColorBlock": 100,
      "IconHint": "voluptas",
      "Selected": false,
      "LastChanged": "2008-12-17T12:19:45.6328079+01:00",
      "ChildItems": [
        {},
        {}
      ],
      "ExtraInfo": "voluptas",
      "StyleHint": "occaecati",
      "Hidden": false,
      "FullName": "Reinhold Glover"
    }
  ],
  "Consents": [
    {
      "ConsentPersonId": 400,
      "Comment": "ullam",
      "Registered": "2009-10-07T12:19:45.6328079+02:00",
      "RegisteredAssociateId": 362,
      "Updated": "2006-02-08T12:19:45.6328079+01:00",
      "UpdatedAssociateId": 112,
      "LegalBaseId": 366,
      "LegalBaseKey": "et",
      "LegalBaseName": "Treutel-Koch",
      "ConsentPurposeId": 761,
      "ConsentPurposeKey": "vel",
      "ConsentPurposeName": "Sawayn, Nader and Padberg",
      "ConsentSourceId": 910,
      "ConsentSourceKey": "accusamus",
      "ConsentSourceName": "Wisozk-Bogan"
    }
  ],
  "BounceEmails": [
    "isai@schmidtwatsica.com",
    "idella@kuvalis.ca"
  ],
  "ActiveStatusMonitorId": 137,
  "UserDefinedFields": {
    "SuperOffice:1": "Prof. Minerva Alfonso Goodwin",
    "SuperOffice:2": "1259586340"
  },
  "ExtraFields": {
    "ExtraFields1": "facere",
    "ExtraFields2": "reprehenderit"
  },
  "CustomFields": {
    "CustomFields1": "veniam",
    "CustomFields2": "alias"
  }
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "PersonId": 315,
  "Firstname": "Pierce",
  "MiddleName": "Pfannerstill-Legros",
  "Lastname": "Morar",
  "Mrmrs": "totam",
  "Title": "minus",
  "UpdatedDate": "2000-04-02T12:19:45.6328079+02:00",
  "CreatedDate": "2021-06-07T12:19:45.6328079+02:00",
  "BirthDate": "2013-04-13T12:19:45.6328079+02:00",
  "CreatedBy": null,
  "Emails": [
    {
      "Value": "aliquid",
      "StrippedValue": "porro",
      "Description": "Multi-tiered attitude-oriented forecast",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 840
        }
      }
    },
    {
      "Value": "aliquid",
      "StrippedValue": "porro",
      "Description": "Multi-tiered attitude-oriented forecast",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 840
        }
      }
    }
  ],
  "Description": "Optional zero defect Graphical User Interface",
  "IsAssociate": true,
  "PrivatePhones": [
    {
      "Value": "id",
      "StrippedValue": "eum",
      "Description": "Total discrete intranet",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 194
        }
      }
    },
    {
      "Value": "id",
      "StrippedValue": "eum",
      "Description": "Total discrete intranet",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 194
        }
      }
    }
  ],
  "Faxes": [
    {
      "Value": "molestiae",
      "StrippedValue": "in",
      "Description": "Virtual global system engine",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 940
        }
      }
    },
    {
      "Value": "molestiae",
      "StrippedValue": "in",
      "Description": "Virtual global system engine",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 940
        }
      }
    }
  ],
  "MobilePhones": [
    {
      "Value": "iure",
      "StrippedValue": "fugit",
      "Description": "Decentralized didactic superstructure",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 697
        }
      }
    },
    {
      "Value": "iure",
      "StrippedValue": "fugit",
      "Description": "Decentralized didactic superstructure",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 697
        }
      }
    }
  ],
  "OfficePhones": [
    {
      "Value": "voluptas",
      "StrippedValue": "voluptatem",
      "Description": "Object-based methodical product",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 736
        }
      }
    },
    {
      "Value": "voluptas",
      "StrippedValue": "voluptatem",
      "Description": "Object-based methodical product",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 736
        }
      }
    }
  ],
  "OtherPhones": [
    {
      "Value": "quia",
      "StrippedValue": "aut",
      "Description": "User-friendly hybrid extranet",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 706
        }
      }
    },
    {
      "Value": "quia",
      "StrippedValue": "aut",
      "Description": "User-friendly hybrid extranet",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 706
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
      "Id": 77,
      "Name": "Hilll, Harber and Goldner",
      "ToolTip": "Molestias dolor culpa ratione esse.",
      "Deleted": false,
      "Rank": 428,
      "Type": "qui",
      "ColorBlock": 984,
      "IconHint": "nihil",
      "Selected": false,
      "LastChanged": "2000-02-12T12:19:45.6328079+01:00",
      "ChildItems": [
        {},
        {}
      ],
      "ExtraInfo": "ducimus",
      "StyleHint": "est",
      "Hidden": true,
      "FullName": "Prof. Tianna Stefan Jacobs",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 31
        }
      }
    }
  ],
  "PersonNumber": "1015181",
  "FullName": "Holly Rusty Steuber DDS",
  "NoMailing": true,
  "UsePersonAddress": true,
  "Retired": true,
  "Urls": [
    {
      "Value": "commodi",
      "StrippedValue": "molestias",
      "Description": "Configurable homogeneous Graphic Interface",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 161
        }
      }
    },
    {
      "Value": "commodi",
      "StrippedValue": "molestias",
      "Description": "Configurable homogeneous Graphic Interface",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 161
        }
      }
    }
  ],
  "FormalName": "Labadie, Ondricka and Marquardt",
  "Address": null,
  "Post3": "ab",
  "Post2": "itaque",
  "Post1": "porro",
  "Kanalname": "distinctio",
  "Kanafname": "hic",
  "CorrespondingAssociate": null,
  "Category": null,
  "Business": null,
  "Associate": null,
  "Salutation": "eum",
  "ActiveInterests": 91,
  "SupportAssociate": null,
  "TicketPriority": null,
  "CustomerLanguage": null,
  "DbiAgentId": 746,
  "DbiKey": "dolore",
  "DbiLastModified": "2014-03-06T12:19:45.6484271+01:00",
  "DbiLastSyncronized": "2003-11-29T12:19:45.6484271+01:00",
  "SentInfo": 506,
  "ShowContactTickets": 384,
  "UserInfo": null,
  "ChatEmails": [
    {
      "Value": "ut",
      "StrippedValue": "delectus",
      "Description": "Cloned bandwidth-monitored instruction set",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 876
        }
      }
    },
    {
      "Value": "ut",
      "StrippedValue": "delectus",
      "Description": "Cloned bandwidth-monitored instruction set",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 876
        }
      }
    }
  ],
  "InternetPhones": [
    {
      "Value": "aut",
      "StrippedValue": "dolores",
      "Description": "Innovative static utilisation",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 256
        }
      }
    },
    {
      "Value": "aut",
      "StrippedValue": "dolores",
      "Description": "Innovative static utilisation",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 256
        }
      }
    }
  ],
  "Source": 223,
  "ActiveErpLinks": 965,
  "ShipmentTypes": [
    {
      "Id": 403,
      "Name": "Cummings Group",
      "ToolTip": "Hic itaque ipsa qui.",
      "Deleted": true,
      "Rank": 28,
      "Type": "laboriosam",
      "ColorBlock": 515,
      "IconHint": "delectus",
      "Selected": false,
      "LastChanged": "2019-10-23T12:19:45.6484271+02:00",
      "ChildItems": [
        {},
        {}
      ],
      "ExtraInfo": "ipsam",
      "StyleHint": "rem",
      "Hidden": false,
      "FullName": "Walton Gleason",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 999
        }
      }
    }
  ],
  "Consents": [
    {
      "ConsentPersonId": 222,
      "Comment": "aliquam",
      "Registered": "2016-04-24T12:19:45.6484271+02:00",
      "RegisteredAssociateId": 173,
      "Updated": "2000-01-23T12:19:45.6484271+01:00",
      "UpdatedAssociateId": 855,
      "LegalBaseId": 430,
      "LegalBaseKey": "non",
      "LegalBaseName": "Zboncak Group",
      "ConsentPurposeId": 215,
      "ConsentPurposeKey": "temporibus",
      "ConsentPurposeName": "Rath, Dickens and Mills",
      "ConsentSourceId": 711,
      "ConsentSourceKey": "culpa",
      "ConsentSourceName": "Beer Inc and Sons",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 526
        }
      }
    }
  ],
  "BounceEmails": [
    "bart_okuneva@oberbrunner.info",
    "guy_ledner@lehnerkonopelski.ca"
  ],
  "ActiveStatusMonitorId": 998,
  "UserDefinedFields": {
    "SuperOffice:1": "982019938",
    "SuperOffice:2": "False"
  },
  "ExtraFields": {
    "ExtraFields1": "voluptatem",
    "ExtraFields2": "alias"
  },
  "CustomFields": {
    "CustomFields1": "et",
    "CustomFields2": "ab"
  },
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.String",
      "FieldLength": 389
    }
  }
}
```