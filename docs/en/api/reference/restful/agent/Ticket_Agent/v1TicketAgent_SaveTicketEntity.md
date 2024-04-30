---
title: POST Agents/Ticket/SaveTicketEntity
uid: v1TicketAgent_SaveTicketEntity
generated: true
---

# POST Agents/Ticket/SaveTicketEntity

```http
POST /api/v1/Agents/Ticket/SaveTicketEntity
```

Updates the existing TicketEntity or creates a new TicketEntity if the id parameter is empty








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

The TicketEntity to be saved. 

| Property Name | Type |  Description |
|----------------|------|--------------|
| TicketId | Integer | The primary key (auto-incremented) |
| Title | String | The title of the ticket. |
| CreatedAt | String | When the ticket was created. |
| LastChanged | String | The last time the ticket was modified. |
| ReadByOwner | String | The datetime for when the ticket last was read by the owner. |
| ReadByCustomer | String | The datetime for when the ticket was read by the customer. |
| FirstReadByOwner | String | The datetime for when the ticket first was read by the current owner. |
| FirstReadByUser | String | The datetime for when the ticket first was read by a user. |
| Activate | String | When the ticket should be activated, if it is postponed. |
| ClosedAt | String | When the ticket was closed. |
| RepliedAt | String | The datetime for when the ticket was replied to. I.e. the first external message added to the ticket. |
| AlertTimeout | String | The datetime for when the ticket should jump to the next alert_level. |
| Deadline | String | Deadline for ticket. |
| CreatedBy | Associate | The associate who created this ticket |
| Author | String | A string representing the author of the ticket (same as author of first message). |
| OwnedBy | Associate | The associate who owns this ticket. Setting the id to 0 will make the ticket unassigned. Setting the id to 2147483647 (MaxInt) will make it automatically assigned according to the ticket category assignment rules.  <para>Use MDO List name "associate" to get list items.</para> |
| Category | TicketCategoryEntity | The ticket category entity which this ticket is connected to  <para>Use MDO List name "ejcategory" to get list items.</para> |
| Slevel | String | The securitylevel of the ticket. |
| Priority | TicketPriorityEntity | The ticket priority entity which this ticket is connected to  <para>Use MDO List name "ticketpriority" to get list items.</para> |
| BaseStatus | String | The status of the ticket. I.e. active/closed/postponed/deleted  <para>Use MDO List name "ticketstatus" to get list items.</para> |
| Status | TicketStatusEntity | The ticket status entity which this ticket is connected to  <para>Use MDO List name "ticketstatus" to get list items.</para> |
| Origin | String | What is the origin of this ticket |
| Person | Person | The primary person that this ticket is connected to  <para>Use MDO List name "person_new" to get list items.</para> |
| SecondaryPersons | Array | The secondary persons this ticket is connected to  <para>Use MDO List name "person_new" to get list items.</para> |
| AlertLevel | Integer | The alert level for the ticket. Matches the level value of the ticket_alert table. |
| ConnectId | Integer | If a ticket is connected to another ticket, this field is set to the id of the &amp;apos;master&amp;apos; ticket. |
| ReadStatus | String | Whether the owner has read the ticket or not (red, yellow, green). |
| TimeToReply | Integer | The time (minutes) between when the ticket was created and when it was replied to. Calculated based on priority&amp;apos;s timeframe. |
| RealTimeToReply | Integer | Same as time_to_reply, but not calculated based on priority. |
| TimeToClose | Integer | The time (minutes) between when the ticket was created and when it was closed. Calculated based on priority&amp;apos;s timeframe. |
| RealTimeToClose | Integer | Same as time_to_close, but not calculated based on priority. |
| TimeSpentInternally | Integer | The total time (seconds) within the priority's office hours the ticket has been in an open status (configurable), not including current state |
| TimeSpentExternally | Integer | The total time (seconds) within the priority's office hours the ticket has been in a external waiting status (configurable), not including current state |
| TimeSpentQueue | Integer | The total time (seconds) within the priority's office hours the ticket has been in a queue status, not including current state |
| RealTimeSpentInternally | Integer | The total time (seconds) within 24x7 the ticket has been in an open status (configurable), not including current state |
| RealTimeSpentExternally | Integer | The total time (seconds) within 24x7 the ticket has been in a external waiting status (configurable), not including current state |
| RealTimeSpentQueue | Integer | The total time (seconds) within 24x7 hours the ticket has been in a queue status, not including current state |
| TimeSpent | Integer | The total time (minutes). Aggregated time spent from ticket&amp;apos;s messages. Read-only for external use. |
| HasAttachment | Boolean | Boolean indicating if this ticket has one or more attachments. |
| NumReplies | Integer | The number of replies (messages) to the customer for this request. |
| NumMessages | Integer | The total number of messages for this request. |
| FromAddress | String | The from-address used when this ticket got created, e.g. by email |
| Messages | Array | TicketMessageId,CreatedAt,SLevel and Important for all the messages connected to this ticket. For message body see the TicketMessageEntity or the TicketMessage archive. |
| Tags | Array | An array containing the tags assigned to this request |
| Language | String | The language of the first external message |
| Sentiment | Integer | The sentiment index of the last external message |
| SentimentConfidence | Integer | The sentiment confidence of the last external message |
| SuggestedCategoryId | Integer | Suggestion for categorization, based on the text of the message (AI) |
| SuggestedCategoryName | String | Suggested category from AI |
| OrigHumanCategoryId | Integer | Will contain the category id selected by the user, when having the choice of using the suggested category or manually selecting a category |
| IconHint | String | Icon representing ticket's state |
| Sale | Sale | The sale that this ticket is connected to  <para>Use MDO List name "sale" to get list items.</para> |
| Project | Project | The project that this ticket is connected to  <para>Use MDO List name "project" to get list items.</para> |
| FormSubmission | TicketFormSubmission | The form submission that this ticket is connected to |
| TicketType | TicketType | Type of the Request  <para>Use MDO List name "TicketType" to get list items.</para> |
| ActiveStatusMonitorId | Integer | Active status monitor identity for related contact. This is a read-only property and is ignored on Save |
| ExtraFields | Object | Deprecated: Use {SuperOffice.CRM.Services.TicketEntity.CustomFields} instead. Extra fields added to the carrier. This could be data from Plug-ins, the foreign key system, external applications, etc. |
| CustomFields | Object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.TicketEntity.ExtraFields} and <see cref="!:UserDefinedFields">UserDefinedFields</see> properties are deprecated in favor of this combined collection. |

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
POST /api/v1/Agents/Ticket/SaveTicketEntity
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: *
Content-Type: application/json; charset=utf-8

{
  "TicketId": 121,
  "Title": "voluptatem",
  "CreatedAt": "2022-04-01T11:16:09.8665963+02:00",
  "LastChanged": "2014-05-30T11:16:09.8665963+02:00",
  "ReadByOwner": "2018-03-22T11:16:09.8665963+01:00",
  "ReadByCustomer": "2000-08-24T11:16:09.8665963+02:00",
  "FirstReadByOwner": "2015-07-08T11:16:09.8665963+02:00",
  "FirstReadByUser": "2003-07-12T11:16:09.8665963+02:00",
  "Activate": "2017-07-09T11:16:09.8665963+02:00",
  "ClosedAt": "2017-01-01T11:16:09.8665963+01:00",
  "RepliedAt": "2018-08-19T11:16:09.8665963+02:00",
  "AlertTimeout": "2019-11-11T11:16:09.8665963+01:00",
  "Deadline": "2013-02-12T11:16:09.8665963+01:00",
  "CreatedBy": null,
  "Author": "sit",
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
      "Position": "voluptate",
      "PersonId": 875,
      "Mrmrs": "et",
      "Firstname": "Simone",
      "Lastname": "Torp",
      "MiddleName": "Yundt Inc and Sons",
      "Title": "amet",
      "Description": "Customer-focused tertiary concept",
      "Email": "bruce_larkin@watersschumm.co.uk",
      "FullName": "Pauline Pouros",
      "DirectPhone": "(115)789-4555",
      "FormalName": "Stanton LLC",
      "CountryId": 943,
      "ContactId": 643,
      "ContactName": "Stroman-McDermott",
      "Retired": 222,
      "Rank": 386,
      "ActiveInterests": 17,
      "ContactDepartment": "",
      "ContactCountryId": 356,
      "ContactOrgNr": "773188",
      "FaxPhone": "575-741-0581 x1963",
      "MobilePhone": "1-458-332-3714 x704",
      "ContactPhone": "798.011.4128 x5058",
      "AssociateName": "O'Keefe LLC",
      "AssociateId": 665,
      "UsePersonAddress": true,
      "ContactFax": "et",
      "Kanafname": "atque",
      "Kanalname": "sed",
      "Post1": "eaque",
      "Post2": "quam",
      "Post3": "ducimus",
      "EmailName": "rory_sanford@oberbrunner.us",
      "ContactFullName": "Samir Haag",
      "ActiveErpLinks": 383,
      "TicketPriorityId": 455,
      "SupportLanguageId": 954,
      "SupportAssociateId": 236,
      "CategoryName": "VIP Customer"
    }
  ],
  "AlertLevel": 247,
  "ConnectId": 43,
  "ReadStatus": "Green",
  "TimeToReply": 10,
  "RealTimeToReply": 711,
  "TimeToClose": 216,
  "RealTimeToClose": 962,
  "TimeSpentInternally": 977,
  "TimeSpentExternally": 177,
  "TimeSpentQueue": 87,
  "RealTimeSpentInternally": 721,
  "RealTimeSpentExternally": 159,
  "RealTimeSpentQueue": 284,
  "TimeSpent": 330,
  "HasAttachment": false,
  "NumReplies": 713,
  "NumMessages": 581,
  "FromAddress": "nobis",
  "Messages": [
    {
      "TicketMessageId": 316,
      "CreatedAt": "2021-02-17T11:16:09.8665963+01:00",
      "Slevel": "External",
      "Important": true,
      "Author": "enim",
      "PersonId": 637,
      "PersonFullName": "Ms. Judge Brown II",
      "ContactId": 13,
      "ContactName": "Carroll Inc and Sons",
      "ContactDepartment": "",
      "NumAttachments": 995,
      "EmailHeader": "kiarra.jenkins@wintheiserschneider.co.uk",
      "MessageHeaders": [
        {},
        {}
      ],
      "Language": "dolore",
      "Sentiment": 883,
      "SentimentConfidence": 626,
      "CreatedBy": 166,
      "ChangedAt": "2010-10-29T11:16:09.8665963+02:00",
      "Badge": "Comment"
    }
  ],
  "Tags": [
    {
      "Id": 895,
      "Name": "Bednar, Kshlerin and Mayert",
      "ToolTip": "Tenetur voluptatem provident voluptas aspernatur enim expedita."
    },
    {
      "Id": 895,
      "Name": "Bednar, Kshlerin and Mayert",
      "ToolTip": "Tenetur voluptatem provident voluptas aspernatur enim expedita."
    }
  ],
  "Language": "quas",
  "Sentiment": 885,
  "SentimentConfidence": 51,
  "SuggestedCategoryId": 810,
  "SuggestedCategoryName": "VIP Customer",
  "OrigHumanCategoryId": 411,
  "IconHint": "et",
  "Sale": null,
  "Project": null,
  "FormSubmission": null,
  "TicketType": null,
  "ActiveStatusMonitorId": 476,
  "ExtraFields": {
    "ExtraFields1": "dolores",
    "ExtraFields2": "praesentium"
  },
  "CustomFields": {
    "CustomFields1": "eveniet",
    "CustomFields2": "ducimus"
  }
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "TicketId": 657,
  "Title": "et",
  "CreatedAt": "2020-09-25T11:16:09.8665963+02:00",
  "LastChanged": "2001-01-25T11:16:09.8665963+01:00",
  "ReadByOwner": "2002-10-13T11:16:09.8665963+02:00",
  "ReadByCustomer": "2007-12-11T11:16:09.8665963+01:00",
  "FirstReadByOwner": "2013-09-22T11:16:09.8665963+02:00",
  "FirstReadByUser": "2008-11-08T11:16:09.8665963+01:00",
  "Activate": "2006-01-29T11:16:09.8665963+01:00",
  "ClosedAt": "2014-07-29T11:16:09.8665963+02:00",
  "RepliedAt": "2000-08-15T11:16:09.8665963+02:00",
  "AlertTimeout": "2020-08-19T11:16:09.8665963+02:00",
  "Deadline": "2006-11-30T11:16:09.8665963+01:00",
  "CreatedBy": null,
  "Author": "officia",
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
      "Position": "ad",
      "PersonId": 248,
      "Mrmrs": "officiis",
      "Firstname": "Imogene",
      "Lastname": "Turcotte",
      "MiddleName": "Hauck Inc and Sons",
      "Title": "occaecati",
      "Description": "Distributed system-worthy adapter",
      "Email": "korey@reichel.name",
      "FullName": "Mrs. Yolanda Tobin Funk",
      "DirectPhone": "443.145.5798 x441",
      "FormalName": "Rogahn LLC",
      "CountryId": 334,
      "ContactId": 861,
      "ContactName": "Beahan Inc and Sons",
      "Retired": 898,
      "Rank": 560,
      "ActiveInterests": 908,
      "ContactDepartment": "",
      "ContactCountryId": 629,
      "ContactOrgNr": "1187465",
      "FaxPhone": "1-851-004-4479 x729",
      "MobilePhone": "436.154.7631",
      "ContactPhone": "1-642-899-8721",
      "AssociateName": "Marvin, White and Hintz",
      "AssociateId": 243,
      "UsePersonAddress": false,
      "ContactFax": "accusamus",
      "Kanafname": "consequatur",
      "Kanalname": "qui",
      "Post1": "et",
      "Post2": "ducimus",
      "Post3": "commodi",
      "EmailName": "timmothy@crona.us",
      "ContactFullName": "Mrs. Felton Lazaro Grant DVM",
      "ActiveErpLinks": 815,
      "TicketPriorityId": 6,
      "SupportLanguageId": 320,
      "SupportAssociateId": 689,
      "CategoryName": "VIP Customer",
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
  "AlertLevel": 376,
  "ConnectId": 322,
  "ReadStatus": "Green",
  "TimeToReply": 329,
  "RealTimeToReply": 746,
  "TimeToClose": 832,
  "RealTimeToClose": 28,
  "TimeSpentInternally": 428,
  "TimeSpentExternally": 808,
  "TimeSpentQueue": 674,
  "RealTimeSpentInternally": 773,
  "RealTimeSpentExternally": 515,
  "RealTimeSpentQueue": 682,
  "TimeSpent": 261,
  "HasAttachment": true,
  "NumReplies": 501,
  "NumMessages": 809,
  "FromAddress": "molestias",
  "Messages": [
    {
      "TicketMessageId": 16,
      "CreatedAt": "2012-12-18T11:16:09.8665963+01:00",
      "Slevel": "External",
      "Important": false,
      "Author": "quo",
      "PersonId": 703,
      "PersonFullName": "Rocky Kovacek",
      "ContactId": 31,
      "ContactName": "Wyman LLC",
      "ContactDepartment": "",
      "NumAttachments": 310,
      "EmailHeader": "giuseppe.schuster@lockman.com",
      "MessageHeaders": [
        {},
        {}
      ],
      "Language": "beatae",
      "Sentiment": 708,
      "SentimentConfidence": 934,
      "CreatedBy": 667,
      "ChangedAt": "1999-02-15T11:16:09.8665963+01:00",
      "Badge": "Comment",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 743
        }
      }
    }
  ],
  "Tags": [
    {
      "Id": 440,
      "Name": "Brakus LLC",
      "ToolTip": "Eius sint quibusdam.",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 225
        }
      }
    },
    {
      "Id": 440,
      "Name": "Brakus LLC",
      "ToolTip": "Eius sint quibusdam.",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 225
        }
      }
    }
  ],
  "Language": "quia",
  "Sentiment": 42,
  "SentimentConfidence": 360,
  "SuggestedCategoryId": 357,
  "SuggestedCategoryName": "VIP Customer",
  "OrigHumanCategoryId": 505,
  "IconHint": "molestiae",
  "Sale": null,
  "Project": null,
  "FormSubmission": null,
  "TicketType": null,
  "ActiveStatusMonitorId": 356,
  "ExtraFields": {
    "ExtraFields1": "in",
    "ExtraFields2": "earum"
  },
  "CustomFields": {
    "CustomFields1": "totam",
    "CustomFields2": "dicta"
  },
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 303
    }
  }
}
```