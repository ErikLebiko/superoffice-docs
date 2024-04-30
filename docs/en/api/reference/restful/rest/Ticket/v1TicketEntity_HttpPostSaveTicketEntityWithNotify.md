---
title: POST Ticket
uid: v1TicketEntity_HttpPostSaveTicketEntityWithNotify
generated: true
---

# POST Ticket

```http
POST /api/v1/Ticket
```

Saves a ticket and performs any user notifications







## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| notify | bool |  If true, then the notifications will be sent |

```http
POST /api/v1/Ticket?notify=False
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

The ticket to save 

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
POST /api/v1/Ticket
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: *
Content-Type: application/json; charset=utf-8

{
  "TicketId": 290,
  "Title": "sit",
  "CreatedAt": "2020-03-26T11:44:42.5701365+01:00",
  "LastChanged": "2018-11-07T11:44:42.5701365+01:00",
  "ReadByOwner": "2001-04-14T11:44:42.5701365+02:00",
  "ReadByCustomer": "1998-09-19T11:44:42.5701365+02:00",
  "FirstReadByOwner": "2021-03-15T11:44:42.5701365+01:00",
  "FirstReadByUser": "2014-12-05T11:44:42.5701365+01:00",
  "Activate": "1999-10-07T11:44:42.5701365+02:00",
  "ClosedAt": "2022-03-27T11:44:42.5701365+02:00",
  "RepliedAt": "1997-12-19T11:44:42.5701365+01:00",
  "AlertTimeout": "2021-06-06T11:44:42.5701365+02:00",
  "Deadline": "2005-07-03T11:44:42.5701365+02:00",
  "CreatedBy": null,
  "Author": "velit",
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
      "Position": "ut",
      "PersonId": 40,
      "Mrmrs": "explicabo",
      "Firstname": "Cristina",
      "Lastname": "Hills",
      "MiddleName": "Schmidt-Runolfsdottir",
      "Title": "mollitia",
      "Description": "Reverse-engineered context-sensitive approach",
      "Email": "queenie_boehm@swaniawskispencer.name",
      "FullName": "Karley Pagac I",
      "DirectPhone": "1-434-577-3991 x4419",
      "FormalName": "Schuster Group",
      "CountryId": 67,
      "ContactId": 537,
      "ContactName": "Purdy-Green",
      "Retired": 796,
      "Rank": 688,
      "ActiveInterests": 776,
      "ContactDepartment": "",
      "ContactCountryId": 969,
      "ContactOrgNr": "1521789",
      "FaxPhone": "1-996-462-2104 x23419",
      "MobilePhone": "950.416.3076 x04532",
      "ContactPhone": "(449)220-2823 x195",
      "AssociateName": "Lesch, King and Swaniawski",
      "AssociateId": 288,
      "UsePersonAddress": false,
      "ContactFax": "fugit",
      "Kanafname": "est",
      "Kanalname": "nulla",
      "Post1": "officia",
      "Post2": "excepturi",
      "Post3": "quis",
      "EmailName": "ethan_kertzmann@hilllwilliamson.com",
      "ContactFullName": "Kacie Rowe",
      "ActiveErpLinks": 779,
      "TicketPriorityId": 268,
      "SupportLanguageId": 998,
      "SupportAssociateId": 989,
      "CategoryName": "VIP Customer"
    }
  ],
  "AlertLevel": 333,
  "ConnectId": 333,
  "ReadStatus": "Green",
  "TimeToReply": 537,
  "RealTimeToReply": 229,
  "TimeToClose": 97,
  "RealTimeToClose": 914,
  "TimeSpentInternally": 197,
  "TimeSpentExternally": 646,
  "TimeSpentQueue": 532,
  "RealTimeSpentInternally": 534,
  "RealTimeSpentExternally": 667,
  "RealTimeSpentQueue": 409,
  "TimeSpent": 58,
  "HasAttachment": false,
  "NumReplies": 588,
  "NumMessages": 227,
  "FromAddress": "voluptatem",
  "Messages": [
    {
      "TicketMessageId": 491,
      "CreatedAt": "2004-06-10T11:44:42.5701365+02:00",
      "Slevel": "External",
      "Important": false,
      "Author": "sunt",
      "PersonId": 685,
      "PersonFullName": "Mr. Xzavier Shanelle Wehner Jr.",
      "ContactId": 831,
      "ContactName": "Wilderman-Hermann",
      "ContactDepartment": "",
      "NumAttachments": 517,
      "EmailHeader": "lester.volkman@sanfordchristiansen.biz",
      "MessageHeaders": [
        {},
        {}
      ],
      "Language": "possimus",
      "Sentiment": 78,
      "SentimentConfidence": 38,
      "CreatedBy": 873,
      "ChangedAt": "2020-07-07T11:44:42.5701365+02:00",
      "Badge": "Comment"
    }
  ],
  "Tags": [
    {
      "Id": 582,
      "Name": "Frami LLC",
      "ToolTip": "Facilis ut."
    },
    {
      "Id": 582,
      "Name": "Frami LLC",
      "ToolTip": "Facilis ut."
    }
  ],
  "Language": "fugit",
  "Sentiment": 570,
  "SentimentConfidence": 518,
  "SuggestedCategoryId": 148,
  "SuggestedCategoryName": "VIP Customer",
  "OrigHumanCategoryId": 577,
  "IconHint": "laudantium",
  "Sale": null,
  "Project": null,
  "FormSubmission": null,
  "TicketType": null,
  "ActiveStatusMonitorId": 676,
  "ExtraFields": {
    "ExtraFields1": "quia",
    "ExtraFields2": "itaque"
  },
  "CustomFields": {
    "CustomFields1": "eum",
    "CustomFields2": "ut"
  }
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "TicketId": 584,
  "Title": "vero",
  "CreatedAt": "2009-07-08T11:44:42.5857526+02:00",
  "LastChanged": "2004-04-13T11:44:42.5857526+02:00",
  "ReadByOwner": "2018-07-14T11:44:42.5857526+02:00",
  "ReadByCustomer": "2000-05-04T11:44:42.5857526+02:00",
  "FirstReadByOwner": "2000-10-18T11:44:42.5857526+02:00",
  "FirstReadByUser": "2014-05-30T11:44:42.5857526+02:00",
  "Activate": "2022-07-25T11:44:42.5857526+02:00",
  "ClosedAt": "2000-10-04T11:44:42.5857526+02:00",
  "RepliedAt": "2015-07-26T11:44:42.5857526+02:00",
  "AlertTimeout": "2003-08-10T11:44:42.5857526+02:00",
  "Deadline": "2009-01-05T11:44:42.5857526+01:00",
  "CreatedBy": null,
  "Author": "corporis",
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
      "Position": "repudiandae",
      "PersonId": 742,
      "Mrmrs": "saepe",
      "Firstname": "Luisa",
      "Lastname": "Kunze",
      "MiddleName": "Morissette-Paucek",
      "Title": "maiores",
      "Description": "Horizontal fresh-thinking architecture",
      "Email": "serenity_armstrong@littel.name",
      "FullName": "Prof. Gregory Yundt",
      "DirectPhone": "(542)928-2367",
      "FormalName": "Muller, Reichert and Murphy",
      "CountryId": 816,
      "ContactId": 806,
      "ContactName": "Altenwerth Group",
      "Retired": 936,
      "Rank": 257,
      "ActiveInterests": 633,
      "ContactDepartment": "",
      "ContactCountryId": 802,
      "ContactOrgNr": "905449",
      "FaxPhone": "(705)981-2339 x834",
      "MobilePhone": "1-408-092-8060 x3522",
      "ContactPhone": "1-964-214-5313 x04084",
      "AssociateName": "Luettgen Group",
      "AssociateId": 546,
      "UsePersonAddress": false,
      "ContactFax": "doloremque",
      "Kanafname": "optio",
      "Kanalname": "eligendi",
      "Post1": "dignissimos",
      "Post2": "dolore",
      "Post3": "excepturi",
      "EmailName": "julius.lind@homenickkautzer.info",
      "ContactFullName": "Broderick Dicki Sr.",
      "ActiveErpLinks": 309,
      "TicketPriorityId": 336,
      "SupportLanguageId": 672,
      "SupportAssociateId": 670,
      "CategoryName": "VIP Customer",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 569
        }
      }
    }
  ],
  "AlertLevel": 309,
  "ConnectId": 128,
  "ReadStatus": "Green",
  "TimeToReply": 27,
  "RealTimeToReply": 867,
  "TimeToClose": 754,
  "RealTimeToClose": 972,
  "TimeSpentInternally": 458,
  "TimeSpentExternally": 830,
  "TimeSpentQueue": 468,
  "RealTimeSpentInternally": 573,
  "RealTimeSpentExternally": 849,
  "RealTimeSpentQueue": 73,
  "TimeSpent": 111,
  "HasAttachment": true,
  "NumReplies": 28,
  "NumMessages": 667,
  "FromAddress": "amet",
  "Messages": [
    {
      "TicketMessageId": 573,
      "CreatedAt": "2016-05-07T11:44:42.5857526+02:00",
      "Slevel": "External",
      "Important": false,
      "Author": "consectetur",
      "PersonId": 3,
      "PersonFullName": "Rozella Steuber",
      "ContactId": 118,
      "ContactName": "Schowalter LLC",
      "ContactDepartment": "",
      "NumAttachments": 808,
      "EmailHeader": "maude@mckenzie.info",
      "MessageHeaders": [
        {},
        {}
      ],
      "Language": "at",
      "Sentiment": 689,
      "SentimentConfidence": 93,
      "CreatedBy": 799,
      "ChangedAt": "2002-10-08T11:44:42.5857526+02:00",
      "Badge": "Comment",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 596
        }
      }
    }
  ],
  "Tags": [
    {
      "Id": 82,
      "Name": "Ortiz Group",
      "ToolTip": "Voluptate magni quis enim libero.",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 2
        }
      }
    },
    {
      "Id": 82,
      "Name": "Ortiz Group",
      "ToolTip": "Voluptate magni quis enim libero.",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 2
        }
      }
    }
  ],
  "Language": "quo",
  "Sentiment": 266,
  "SentimentConfidence": 164,
  "SuggestedCategoryId": 454,
  "SuggestedCategoryName": "VIP Customer",
  "OrigHumanCategoryId": 550,
  "IconHint": "commodi",
  "Sale": null,
  "Project": null,
  "FormSubmission": null,
  "TicketType": null,
  "ActiveStatusMonitorId": 365,
  "ExtraFields": {
    "ExtraFields1": "cupiditate",
    "ExtraFields2": "voluptatibus"
  },
  "CustomFields": {
    "CustomFields1": "temporibus",
    "CustomFields2": "illum"
  },
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 458
    }
  }
}
```