---
title: POST Agents/Ticket/GetNextInQueue
uid: v1TicketAgent_GetNextInQueue
generated: true
---

# POST Agents/Ticket/GetNextInQueue

```http
POST /api/v1/Agents/Ticket/GetNextInQueue
```

Assign a ticket to the caller based on intelligent queue system







## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category". Default = show all fields. |

```http
POST /api/v1/Agents/Ticket/GetNextInQueue?$select=name,department,category/id
```


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
POST /api/v1/Agents/Ticket/GetNextInQueue
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: sv
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "TicketId": 635,
  "Title": "saepe",
  "CreatedAt": "2003-01-13T04:22:27.9287467+01:00",
  "LastChanged": "2011-06-25T04:22:27.9287467+02:00",
  "ReadByOwner": "2003-10-04T04:22:27.9287467+02:00",
  "ReadByCustomer": "2019-03-19T04:22:27.9287467+01:00",
  "FirstReadByOwner": "2009-04-29T04:22:27.9287467+02:00",
  "FirstReadByUser": "2019-09-25T04:22:27.9287467+02:00",
  "Activate": "2003-03-01T04:22:27.9287467+01:00",
  "ClosedAt": "1999-08-16T04:22:27.9287467+02:00",
  "RepliedAt": "2005-12-21T04:22:27.9287467+01:00",
  "AlertTimeout": "2011-04-23T04:22:27.9287467+02:00",
  "Deadline": "2019-07-04T04:22:27.9287467+02:00",
  "CreatedBy": null,
  "Author": "harum",
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
      "Position": "fuga",
      "PersonId": 858,
      "Mrmrs": "dolorem",
      "Firstname": "Helena",
      "Lastname": "Stroman",
      "MiddleName": "Christiansen-Rippin",
      "Title": "sit",
      "Description": "Customer-focused full-range standardization",
      "Email": "chanelle_kessler@parisian.name",
      "FullName": "Rebeca Judge DuBuque Jr.",
      "DirectPhone": "1-133-612-5489 x8262",
      "FormalName": "Wisozk-Simonis",
      "CountryId": 827,
      "ContactId": 241,
      "ContactName": "Bednar, Predovic and Keebler",
      "Retired": 705,
      "Rank": 436,
      "ActiveInterests": 1000,
      "ContactDepartment": "",
      "ContactCountryId": 938,
      "ContactOrgNr": "903934",
      "FaxPhone": "(555)003-0590",
      "MobilePhone": "646.071.2832 x61161",
      "ContactPhone": "336.151.0265 x246",
      "AssociateName": "Considine Inc and Sons",
      "AssociateId": 993,
      "UsePersonAddress": false,
      "ContactFax": "natus",
      "Kanafname": "eos",
      "Kanalname": "qui",
      "Post1": "quaerat",
      "Post2": "labore",
      "Post3": "numquam",
      "EmailName": "shyanne@marksernser.com",
      "ContactFullName": "Denis Cruickshank",
      "ActiveErpLinks": 919,
      "TicketPriorityId": 104,
      "SupportLanguageId": 715,
      "SupportAssociateId": 454,
      "CategoryName": "VIP Customer",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 649
        }
      }
    }
  ],
  "AlertLevel": 410,
  "ConnectId": 771,
  "ReadStatus": "Green",
  "TimeToReply": 437,
  "RealTimeToReply": 227,
  "TimeToClose": 712,
  "RealTimeToClose": 134,
  "TimeSpentInternally": 815,
  "TimeSpentExternally": 9,
  "TimeSpentQueue": 59,
  "RealTimeSpentInternally": 250,
  "RealTimeSpentExternally": 273,
  "RealTimeSpentQueue": 137,
  "TimeSpent": 640,
  "HasAttachment": false,
  "NumReplies": 269,
  "NumMessages": 500,
  "FromAddress": "quo",
  "Messages": [
    {
      "TicketMessageId": 633,
      "CreatedAt": "1998-11-19T04:22:27.9287467+01:00",
      "Slevel": "External",
      "Important": false,
      "Author": "assumenda",
      "PersonId": 282,
      "PersonFullName": "Miss Florine Beth Schuppe",
      "ContactId": 623,
      "ContactName": "Hirthe-Kuhn",
      "ContactDepartment": "",
      "NumAttachments": 621,
      "EmailHeader": "karl@hilllmetz.biz",
      "MessageHeaders": [
        {},
        {}
      ],
      "Language": "voluptas",
      "Sentiment": 773,
      "SentimentConfidence": 471,
      "CreatedBy": 236,
      "ChangedAt": "2003-07-24T04:22:27.9287467+02:00",
      "Badge": "Comment",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 829
        }
      }
    }
  ],
  "Tags": [
    {
      "Id": 869,
      "Name": "Schmidt Group",
      "ToolTip": "Cum qui voluptatum ut amet fuga at non.",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 279
        }
      }
    },
    {
      "Id": 869,
      "Name": "Schmidt Group",
      "ToolTip": "Cum qui voluptatum ut amet fuga at non.",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 279
        }
      }
    }
  ],
  "Language": "perferendis",
  "Sentiment": 388,
  "SentimentConfidence": 73,
  "SuggestedCategoryId": 694,
  "SuggestedCategoryName": "VIP Customer",
  "OrigHumanCategoryId": 627,
  "IconHint": "qui",
  "Sale": null,
  "Project": null,
  "FormSubmission": null,
  "TicketType": null,
  "ActiveStatusMonitorId": 582,
  "ExtraFields": {
    "ExtraFields1": "accusantium",
    "ExtraFields2": "nam"
  },
  "CustomFields": {
    "CustomFields1": "ut",
    "CustomFields2": "dolorum"
  },
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.String",
      "FieldLength": 481
    }
  }
}
```