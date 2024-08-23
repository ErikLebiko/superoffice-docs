---
title: POST Agents/Ticket/CreateDefaultForTicketType
uid: v1TicketAgent_CreateDefaultForTicketType
generated: true
---

# POST Agents/Ticket/CreateDefaultForTicketType

```http
POST /api/v1/Agents/Ticket/CreateDefaultForTicketType
```

Create default ticket entity for particular TicketType







## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category". Default = show all fields. |

```http
POST /api/v1/Agents/Ticket/CreateDefaultForTicketType?$select=name,department,category/id
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

TicketTypeId 

| Property Name | Type |  Description |
|----------------|------|--------------|
| TicketTypeId | Integer |  |

## Response:

OK

| Response | Description |
|----------------|-------------|
| 200 | OK |

### Response body: TicketEntity

| Property Name | Type |  Description |
|----------------|------|--------------|
| TicketId | int32 | The primary key (auto-incremented) |
| Title | string | The title of the ticket. |
| CreatedAt | date-time | When the ticket was created. |
| LastChanged | date-time | The last time the ticket was modified. |
| ReadByOwner | date-time | The datetime for when the ticket last was read by the owner. |
| ReadByCustomer | date-time | The datetime for when the ticket was read by the customer. |
| FirstReadByOwner | date-time | The datetime for when the ticket first was read by the current owner. |
| FirstReadByUser | date-time | The datetime for when the ticket first was read by a user. |
| Activate | date-time | When the ticket should be activated, if it is postponed. |
| ClosedAt | date-time | When the ticket was closed. |
| RepliedAt | date-time | The datetime for when the ticket was replied to. I.e. the first external message added to the ticket. |
| AlertTimeout | date-time | The datetime for when the ticket should jump to the next alert_level. |
| Deadline | date-time | Deadline for ticket. |
| CreatedBy | Associate | The associate who created this ticket |
| Author | string | A string representing the author of the ticket (same as author of first message). |
| OwnedBy | Associate | The associate who owns this ticket. Setting the id to 0 will make the ticket unassigned. Setting the id to 2147483647 (MaxInt) will make it automatically assigned according to the ticket category assignment rules.  Use MDO List name "associate" to get list items. |
| Category | TicketCategoryEntity | The ticket category entity which this ticket is connected to  Use MDO List name "ejcategory" to get list items. |
| Slevel | string | The securitylevel of the ticket. |
| Priority | TicketPriorityEntity | The ticket priority entity which this ticket is connected to  Use MDO List name "ticketpriority" to get list items. |
| BaseStatus | string | The status of the ticket. I.e. active/closed/postponed/deleted  Use MDO List name "ticketstatus" to get list items. |
| Status | TicketStatusEntity | The ticket status entity which this ticket is connected to  Use MDO List name "ticketstatus" to get list items. |
| Origin | string | What is the origin of this ticket |
| Person | Person | The primary person that this ticket is connected to  Use MDO List name "person_new" to get list items. |
| SecondaryPersons | array | The secondary persons this ticket is connected to  Use MDO List name "person_new" to get list items. |
| AlertLevel | int32 | The alert level for the ticket. Matches the level value of the ticket_alert table. |
| ConnectId | int32 | If a ticket is connected to another ticket, this field is set to the id of the &amp;apos;master&amp;apos; ticket. |
| ReadStatus | string | Whether the owner has read the ticket or not (red, yellow, green). |
| TimeToReply | int32 | The time (minutes) between when the ticket was created and when it was replied to. Calculated based on priority&amp;apos;s timeframe. |
| RealTimeToReply | int32 | Same as time_to_reply, but not calculated based on priority. |
| TimeToClose | int32 | The time (minutes) between when the ticket was created and when it was closed. Calculated based on priority&amp;apos;s timeframe. |
| RealTimeToClose | int32 | Same as time_to_close, but not calculated based on priority. |
| TimeSpentInternally | int32 | The total time (seconds) within the priority's office hours the ticket has been in an open status (configurable), not including current state |
| TimeSpentExternally | int32 | The total time (seconds) within the priority's office hours the ticket has been in a external waiting status (configurable), not including current state |
| TimeSpentQueue | int32 | The total time (seconds) within the priority's office hours the ticket has been in a queue status, not including current state |
| RealTimeSpentInternally | int32 | The total time (seconds) within 24x7 the ticket has been in an open status (configurable), not including current state |
| RealTimeSpentExternally | int32 | The total time (seconds) within 24x7 the ticket has been in a external waiting status (configurable), not including current state |
| RealTimeSpentQueue | int32 | The total time (seconds) within 24x7 hours the ticket has been in a queue status, not including current state |
| TimeSpent | int32 | The total time (minutes). Aggregated time spent from ticket&amp;apos;s messages. Read-only for external use. |
| HasAttachment | bool | Boolean indicating if this ticket has one or more attachments. |
| NumReplies | int32 | The number of replies (messages) to the customer for this request. |
| NumMessages | int32 | The total number of messages for this request. |
| FromAddress | string | The from-address used when this ticket got created, e.g. by email |
| Messages | array | TicketMessageId,CreatedAt,SLevel and Important for all the messages connected to this ticket. For message body see the TicketMessageEntity or the TicketMessage archive. |
| Tags | array | An array containing the tags assigned to this request |
| Language | string | The language of the first external message |
| Sentiment | int32 | The sentiment index of the last external message |
| SentimentConfidence | int32 | The sentiment confidence of the last external message |
| SuggestedCategoryId | int32 | Suggestion for categorization, based on the text of the message (AI) |
| SuggestedCategoryName | string | Suggested category from AI |
| OrigHumanCategoryId | int32 | Will contain the category id selected by the user, when having the choice of using the suggested category or manually selecting a category |
| IconHint | string | Icon representing ticket's state |
| Sale | Sale | The sale that this ticket is connected to  Use MDO List name "sale" to get list items. |
| Project | Project | The project that this ticket is connected to  Use MDO List name "project" to get list items. |
| FormSubmission | TicketFormSubmission | The form submission that this ticket is connected to |
| TicketType | TicketType | Type of the Request  Use MDO List name "TicketType" to get list items. |
| ActiveStatusMonitorId | int32 | Active status monitor identity for related contact. This is a read-only property and is ignored on Save |
| ExtraFields | object | Deprecated: Use {SuperOffice.CRM.Services.TicketEntity.CustomFields} instead. Extra fields added to the carrier. This could be data from Plug-ins, the foreign key system, external applications, etc. |
| CustomFields | object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.TicketEntity.ExtraFields} and UserDefinedFields properties are deprecated in favor of this combined collection. |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |

## Sample request

```http!
POST /api/v1/Agents/Ticket/CreateDefaultForTicketType
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: fr,de,ru,zh
Content-Type: application/json; charset=utf-8

{
  "TicketTypeId": 257
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "TicketId": 913,
  "Title": "itaque",
  "CreatedAt": "2015-01-19T13:28:24.0541522+01:00",
  "LastChanged": "2015-05-04T13:28:24.0541522+02:00",
  "ReadByOwner": "2018-07-07T13:28:24.0541522+02:00",
  "ReadByCustomer": "2000-03-27T13:28:24.0541522+02:00",
  "FirstReadByOwner": "2024-08-03T13:28:24.0541522+02:00",
  "FirstReadByUser": "1997-12-31T13:28:24.0541522+01:00",
  "Activate": "2018-12-06T13:28:24.0541522+01:00",
  "ClosedAt": "2005-02-04T13:28:24.0541522+01:00",
  "RepliedAt": "2011-01-26T13:28:24.0541522+01:00",
  "AlertTimeout": "2017-10-18T13:28:24.0541522+02:00",
  "Deadline": "2006-02-19T13:28:24.0541522+01:00",
  "CreatedBy": null,
  "Author": "hic",
  "OwnedBy": null,
  "Category": null,
  "Slevel": "External",
  "Priority": null,
  "BaseStatus": "Active",
  "Status": null,
  "Origin": "AutoGenerated",
  "Person": null,
  "SecondaryPersons": [
    {
      "Position": "esse",
      "PersonId": 596,
      "Mrmrs": "exercitationem",
      "Firstname": "Herminio",
      "Lastname": "Mayer",
      "MiddleName": "Ortiz-Koss",
      "Title": "sint",
      "Description": "Persevering holistic architecture",
      "Email": "emmy.ondricka@reilly.biz",
      "FullName": "Jenifer Quitzon",
      "DirectPhone": "286-967-8511 x5102",
      "FormalName": "Goldner-Barrows",
      "CountryId": 481,
      "ContactId": 715,
      "ContactName": "Hilpert-Beatty",
      "Retired": 907,
      "Rank": 735,
      "ActiveInterests": 482,
      "ContactDepartment": "",
      "ContactCountryId": 905,
      "ContactOrgNr": "832978",
      "FaxPhone": "(797)500-5422 x67648",
      "MobilePhone": "560.868.1668 x6233",
      "ContactPhone": "383.546.8866 x910",
      "AssociateName": "Quigley-Russel",
      "AssociateId": 116,
      "UsePersonAddress": false,
      "ContactFax": "molestiae",
      "Kanafname": "provident",
      "Kanalname": "velit",
      "Post1": "dolore",
      "Post2": "dolore",
      "Post3": "qui",
      "EmailName": "cali.zieme@cormier.name",
      "ContactFullName": "Mitchell Howell",
      "ActiveErpLinks": 95,
      "TicketPriorityId": 798,
      "SupportLanguageId": 918,
      "SupportAssociateId": 384,
      "CategoryName": "VIP Customer",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 51
        }
      }
    }
  ],
  "AlertLevel": 111,
  "ConnectId": 69,
  "ReadStatus": "Green",
  "TimeToReply": 476,
  "RealTimeToReply": 582,
  "TimeToClose": 2,
  "RealTimeToClose": 144,
  "TimeSpentInternally": 717,
  "TimeSpentExternally": 263,
  "TimeSpentQueue": 781,
  "RealTimeSpentInternally": 392,
  "RealTimeSpentExternally": 889,
  "RealTimeSpentQueue": 317,
  "TimeSpent": 278,
  "HasAttachment": true,
  "NumReplies": 25,
  "NumMessages": 642,
  "FromAddress": "numquam",
  "Messages": [
    {
      "TicketMessageId": 910,
      "CreatedAt": "2004-02-22T13:28:24.0541522+01:00",
      "Slevel": "External",
      "Important": true,
      "Author": "dignissimos",
      "PersonId": 255,
      "PersonFullName": "Zola Rice",
      "ContactId": 643,
      "ContactName": "Wilderman Group",
      "ContactDepartment": "",
      "NumAttachments": 11,
      "EmailHeader": "deshaun@brakus.com",
      "MessageHeaders": [
        {},
        {}
      ],
      "Language": "alias",
      "Sentiment": 406,
      "SentimentConfidence": 232,
      "CreatedBy": 592,
      "ChangedAt": "1999-12-16T13:28:24.0541522+01:00",
      "Badge": "Comment",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 988
        }
      }
    }
  ],
  "Tags": [
    {
      "Id": 810,
      "Name": "Botsford Group",
      "ToolTip": "Aperiam in et odio provident saepe possimus sint.",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 631
        }
      }
    },
    {
      "Id": 810,
      "Name": "Botsford Group",
      "ToolTip": "Aperiam in et odio provident saepe possimus sint.",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 631
        }
      }
    }
  ],
  "Language": "laudantium",
  "Sentiment": 669,
  "SentimentConfidence": 50,
  "SuggestedCategoryId": 311,
  "SuggestedCategoryName": "VIP Customer",
  "OrigHumanCategoryId": 51,
  "IconHint": "perspiciatis",
  "Sale": null,
  "Project": null,
  "FormSubmission": null,
  "TicketType": null,
  "ActiveStatusMonitorId": 114,
  "ExtraFields": {
    "ExtraFields1": "quis",
    "ExtraFields2": "aperiam"
  },
  "CustomFields": {
    "CustomFields1": "ut",
    "CustomFields2": "consequatur"
  },
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 569
    }
  }
}
```