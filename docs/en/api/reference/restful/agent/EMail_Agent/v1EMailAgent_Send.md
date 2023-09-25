---
title: POST Agents/EMail/Send
uid: v1EMailAgent_Send
generated: true
---

# POST Agents/EMail/Send

```http
POST /api/v1/Agents/EMail/Send
```

Send the provided e-mails


## Online Restricted: ## The EMail agent is not available in Online by default. Access must be requested specifically when app is registered.






## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category". Default = show all fields. |

```http
POST /api/v1/Agents/EMail/Send?$select=name,department,category/id
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

Emails 

| Property Name | Type |  Description |
|----------------|------|--------------|
| Emails | Array |  |

## Response:array

OK

| Response | Description |
|----------------|-------------|
| 200 | OK |

### Response body: array

| Property Name | Type |  Description |
|----------------|------|--------------|
| To | array | To recipients of e-mail |
| Cc | array | Cc recipients of e-mail |
| Bcc | array | Bcc recipient of e-mail |
| Subject | string | Subject of the e-mail |
| HTMLBody | string | Body formatted in HTML |
| From | EMailAddress | Who did the e-mail originate from |
| Sent | date-time | When was the e-mail sent |
| Size | int32 | Total size of the e-mail |
| Priority | string | Importance of the e-mail |
| Flags | string | Flag status of this mail (unread, replied, deleted ) |
| MessageID | string | Unique id of e-mails |
| PlainBody | string | Body formatted in plain text |
| IsSent | bool | Is this a sent e-mail (not new) |
| EMailSOInfo | EMailSOInfo | Glue between SuperOffice data and an e-mail. |
| ServerId | int32 | Unique id for the e-mail on the server |
| Attachments | array |  |
| CustomHeaderList | array | Non standard e-mail headers |
| FolderName | string | Name of folder the e-mail belongs in |
| EmailItemId | int32 | Primary key |
| AccountId | int32 | Account Id |
| ReceivedAt | date-time | Received date time |
| InReplyTo | EMailEnvelope | The envelope of the email this email is a reply to, if it exists |
| RepliedAt | date-time | When this email was replied at |
| HasCalendarData | bool | If this email contains exactly one iCal appointment |
| CalMethod | string | Method stored in the associated iCal appointment. Indicates if the iCal data is a reply, counter proposal etc. |
| CalReplyStatus | string | Reply status stored in calendar data for the ical method is REPLY |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |

## Sample request

```http!
POST /api/v1/Agents/EMail/Send
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: fr,de,ru,zh
Content-Type: application/json; charset=utf-8

{
  "Emails": [
    {
      "To": [
        {},
        {}
      ],
      "Cc": [
        {},
        {}
      ],
      "Bcc": [
        {},
        {}
      ],
      "Subject": "possimus",
      "HTMLBody": "perferendis",
      "From": null,
      "Sent": "2000-05-02T03:24:47.705153+02:00",
      "Size": 901,
      "Priority": "High",
      "Flags": "Answered",
      "MessageID": "ipsum",
      "PlainBody": "modi",
      "IsSent": false,
      "EMailSOInfo": null,
      "ServerId": 696,
      "Attachments": [
        {},
        {}
      ],
      "CustomHeaderList": [
        {},
        {}
      ],
      "FolderName": "Kuhn Group",
      "EmailItemId": 700,
      "AccountId": 905,
      "ReceivedAt": "1999-06-16T03:24:47.705153+02:00",
      "InReplyTo": null,
      "RepliedAt": "2021-06-07T03:24:47.705153+02:00",
      "HasCalendarData": false,
      "CalMethod": "Add",
      "CalReplyStatus": "Accepted"
    }
  ]
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
  {
    "To": [
      {
        "ContactId": 7,
        "ContactName": "Kuhic, Grimes and Schiller",
        "PersonId": 828,
        "PersonName": "Little Group",
        "AssociateId": 130,
        "Address": "quidem",
        "EmailId": 772,
        "DuplicatePersonIds": [
          748,
          366
        ],
        "Name": "Abernathy-Cremin",
        "TableRight": null,
        "FieldProperties": {
          "fieldName": {
            "FieldRight": null,
            "FieldType": "System.Int32",
            "FieldLength": 492
          }
        }
      }
    ],
    "Cc": [
      {
        "ContactId": 857,
        "ContactName": "Terry Inc and Sons",
        "PersonId": 893,
        "PersonName": "Considine-Lind",
        "AssociateId": 78,
        "Address": "sunt",
        "EmailId": 560,
        "DuplicatePersonIds": [
          823,
          260
        ],
        "Name": "Connelly LLC",
        "TableRight": null,
        "FieldProperties": {
          "fieldName": {
            "FieldRight": null,
            "FieldType": "System.String",
            "FieldLength": 181
          }
        }
      }
    ],
    "Bcc": [
      {
        "ContactId": 132,
        "ContactName": "O'Conner-Durgan",
        "PersonId": 791,
        "PersonName": "O'Conner Group",
        "AssociateId": 166,
        "Address": "harum",
        "EmailId": 534,
        "DuplicatePersonIds": [
          400,
          419
        ],
        "Name": "Ward Group",
        "TableRight": null,
        "FieldProperties": {
          "fieldName": {
            "FieldRight": null,
            "FieldType": "System.String",
            "FieldLength": 501
          }
        }
      }
    ],
    "Subject": "voluptates",
    "HTMLBody": "sed",
    "From": null,
    "Sent": "2001-06-05T03:24:47.705153+02:00",
    "Size": 155,
    "Priority": "High",
    "Flags": "Answered",
    "MessageID": "recusandae",
    "PlainBody": "amet",
    "IsSent": false,
    "EMailSOInfo": null,
    "ServerId": 371,
    "Attachments": [
      {
        "Description": "Virtual well-modulated groupware",
        "Filename": "eius",
        "Size": 63,
        "Type": "quas",
        "Encoding": "itaque",
        "Id": "illum",
        "Disposition": "id",
        "IsSafeFileExtension": false,
        "Stream": "GIF89....File contents as raw bytes...",
        "TableRight": null,
        "FieldProperties": {
          "fieldName": {
            "FieldRight": null,
            "FieldType": "System.Int32",
            "FieldLength": 492
          }
        }
      }
    ],
    "CustomHeaderList": [
      {
        "Name": "Runolfsson-Wuckert",
        "Values": [
          "laudantium",
          "error"
        ],
        "TableRight": null,
        "FieldProperties": {
          "fieldName": {
            "FieldRight": null,
            "FieldType": "System.Int32",
            "FieldLength": 805
          }
        }
      },
      {
        "Name": "Runolfsson-Wuckert",
        "Values": [
          "laudantium",
          "error"
        ],
        "TableRight": null,
        "FieldProperties": {
          "fieldName": {
            "FieldRight": null,
            "FieldType": "System.Int32",
            "FieldLength": 805
          }
        }
      }
    ],
    "FolderName": "Reynolds, Muller and Barton",
    "EmailItemId": 165,
    "AccountId": 237,
    "ReceivedAt": "2018-08-27T03:24:47.705153+02:00",
    "InReplyTo": null,
    "RepliedAt": "2014-11-20T03:24:47.705153+01:00",
    "HasCalendarData": false,
    "CalMethod": "Add",
    "CalReplyStatus": "Accepted",
    "TableRight": null,
    "FieldProperties": {
      "fieldName": {
        "FieldRight": null,
        "FieldType": "System.Int32",
        "FieldLength": 115
      }
    }
  }
]
```