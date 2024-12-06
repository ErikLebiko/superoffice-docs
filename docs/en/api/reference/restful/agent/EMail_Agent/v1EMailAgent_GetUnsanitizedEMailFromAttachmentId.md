---
title: POST Agents/EMail/GetUnsanitizedEMailFromAttachmentId
uid: v1EMailAgent_GetUnsanitizedEMailFromAttachmentId
generated: true
---

# POST Agents/EMail/GetUnsanitizedEMailFromAttachmentId

```http
POST /api/v1/Agents/EMail/GetUnsanitizedEMailFromAttachmentId
```

Get an e-mail based on an email and attachment id.


The returned value is not sanitized.


## Online Restricted: ## The EMail agent is not available in Online by default. Access must be requested specifically when app is registered.






## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category". Default = show all fields. |

```http
POST /api/v1/Agents/EMail/GetUnsanitizedEMailFromAttachmentId?$select=name,department,category/id
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

EmailId, AttachmentIds, IncludeAttachments 

| Property Name | Type |  Description |
|----------------|------|--------------|
| EmailId | Integer |  |
| AttachmentIds | Array |  |
| IncludeAttachments | Boolean |  |

## Response:

OK

| Response | Description |
|----------------|-------------|
| 200 | OK |

### Response body: EMailEntity

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
POST /api/v1/Agents/EMail/GetUnsanitizedEMailFromAttachmentId
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: en
Content-Type: application/json; charset=utf-8

{
  "EmailId": 387,
  "AttachmentIds": [
    "consequatur",
    "deleniti"
  ],
  "IncludeAttachments": false
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "To": [
    {
      "ContactId": 848,
      "ContactName": "Rohan-Stiedemann",
      "PersonId": 26,
      "PersonName": "Schowalter, Ratke and McGlynn",
      "AssociateId": 532,
      "Address": "enim",
      "EmailId": 911,
      "DuplicatePersonIds": [
        791,
        963
      ],
      "Name": "Cole-Larkin",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 391
        }
      }
    }
  ],
  "Cc": [
    {
      "ContactId": 693,
      "ContactName": "Schimmel-Skiles",
      "PersonId": 687,
      "PersonName": "Watsica, Willms and Huels",
      "AssociateId": 989,
      "Address": "aut",
      "EmailId": 816,
      "DuplicatePersonIds": [
        721,
        249
      ],
      "Name": "Medhurst, Johnson and Bogan",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 634
        }
      }
    }
  ],
  "Bcc": [
    {
      "ContactId": 901,
      "ContactName": "Bernhard-Bernier",
      "PersonId": 959,
      "PersonName": "Steuber-Lesch",
      "AssociateId": 507,
      "Address": "eum",
      "EmailId": 338,
      "DuplicatePersonIds": [
        733,
        931
      ],
      "Name": "Strosin, Hand and Pfeffer",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 959
        }
      }
    }
  ],
  "Subject": "omnis",
  "HTMLBody": "beatae",
  "From": null,
  "Sent": "2014-01-26T10:17:55.5977887+01:00",
  "Size": 762,
  "Priority": "High",
  "Flags": "Answered",
  "MessageID": "est",
  "PlainBody": "repellat",
  "IsSent": false,
  "EMailSOInfo": null,
  "ServerId": 693,
  "Attachments": [
    {
      "Description": "Advanced value-added migration",
      "Filename": "tempora",
      "Size": 869,
      "Type": "quia",
      "Encoding": "in",
      "Id": "et",
      "Disposition": "sed",
      "IsSafeFileExtension": true,
      "Stream": "GIF89....File contents as raw bytes...",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 704
        }
      }
    }
  ],
  "CustomHeaderList": [
    {
      "Name": "Feil, Grimes and Effertz",
      "Values": [
        "perferendis",
        "quae"
      ],
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 613
        }
      }
    },
    {
      "Name": "Feil, Grimes and Effertz",
      "Values": [
        "perferendis",
        "quae"
      ],
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 613
        }
      }
    }
  ],
  "FolderName": "Schmeler Inc and Sons",
  "EmailItemId": 632,
  "AccountId": 936,
  "ReceivedAt": "2012-05-11T10:17:55.5977887+02:00",
  "InReplyTo": null,
  "RepliedAt": "2005-06-09T10:17:55.5977887+02:00",
  "HasCalendarData": false,
  "CalMethod": "Add",
  "CalReplyStatus": "Accepted",
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 89
    }
  }
}
```