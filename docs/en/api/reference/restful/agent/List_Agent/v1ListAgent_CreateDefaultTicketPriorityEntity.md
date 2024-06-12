---
title: POST Agents/List/CreateDefaultTicketPriorityEntity
uid: v1ListAgent_CreateDefaultTicketPriorityEntity
generated: true
---

# POST Agents/List/CreateDefaultTicketPriorityEntity

```http
POST /api/v1/Agents/List/CreateDefaultTicketPriorityEntity
```

Set default values into a new TicketPriorityEntity.


NetServer calculates default values on the entity, which is required when creating/storing a new instance







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

### Response body: TicketPriorityEntity

| Property Name | Type |  Description |
|----------------|------|--------------|
| TicketPriorityId | int32 | The primary key (auto-incremented) |
| Name | string | The name of the priority. |
| Status | string | The status (normal/deleted) of the priority. |
| Flags | string | A bitmask of flags. |
| SortOrder | int32 | Indicates the sort order for this priority. 1 is first, 100 is last |
| TicketRead | string | This field indicates what to do with the escalation chain when the request is read |
| ChangedOwner | string | This field indicates what to do with the escalation chain when the request changes owner (manually) |
| TicketNewinfo | string | This field indicates what to do with the escalation chain when the request gets new info |
| TicketClosed | string | This field indicates what to do with the escalation chain when the request is closed |
| TicketChangedPriority | string | This field indicates what to do with the escalation chain when the request is changed into this priority |
| TicketNew | string | This field indicates what to do with the escalation chain when a new request is registered |
| Deadline | int32 | Deadline to add if escalated (minutes) |
| MonStart | date-time | The work hour start for Mondays. Note that only the time part of the DateTime is used |
| MonStop | date-time | The work hour start for Mondays. Note that only the time part of the DateTime is used |
| TueStart | date-time | The work hour start for Tuesdays. Note that only the time part of the DateTime is used |
| TueStop | date-time | The work hour stop for Tuesdays. Note that only the time part of the DateTime is used |
| WedStart | date-time | The work hour start for Wednesdays. Note that only the time part of the DateTime is used |
| WedStop | date-time | The work hour stop for Wednesdays. Note that only the time part of the DateTime is used |
| ThuStart | date-time | The work hour start for Thursdays. Note that only the time part of the DateTime is used |
| ThuStop | date-time | The work hour stop for Thursdays. Note that only the time part of the DateTime is used |
| FriStart | date-time | The work hour start for Fridays. Note that only the time part of the DateTime is used |
| FriStop | date-time | The work hour stop for Fridays. Note that only the time part of the DateTime is used |
| SatStart | date-time | The work hour start for Saturdays. Note that only the time part of the DateTime is used |
| SatStop | date-time | The work hour stop for Saturdays. Note that only the time part of the DateTime is used |
| SunStart | date-time | The work hour start for Sundays. Note that only the time part of the DateTime is used |
| SunStop | date-time | The work hour stop for Sundays. Note that only the time part of the DateTime is used |
| NonDates | array | Dates which the escalation time should not be running. Note that only the day of the year (day and month) is used. So the year and time part is not used even if this is a DateTime. Exception - it IS possible to include a year here, for dates that should not repeat every year |
| EscalationLevels | array | Escalation levels bound to the parent priority |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |

## Sample request

```http!
POST /api/v1/Agents/List/CreateDefaultTicketPriorityEntity
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: fr,de,ru,zh
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "TicketPriorityId": 25,
  "Name": "Barrows-Oberbrunner",
  "Status": "Deleted",
  "Flags": "AlertSchedule",
  "SortOrder": 806,
  "TicketRead": "Continue",
  "ChangedOwner": "Continue",
  "TicketNewinfo": "Continue",
  "TicketClosed": "Continue",
  "TicketChangedPriority": "Continue",
  "TicketNew": "Continue",
  "Deadline": 658,
  "MonStart": "2008-06-14T04:22:27.0486609+02:00",
  "MonStop": "2006-12-03T04:22:27.0486609+01:00",
  "TueStart": "2020-05-13T04:22:27.0486609+02:00",
  "TueStop": "2003-09-08T04:22:27.0486609+02:00",
  "WedStart": "2000-08-20T04:22:27.0486609+02:00",
  "WedStop": "2003-09-27T04:22:27.0486609+02:00",
  "ThuStart": "2006-02-12T04:22:27.0486609+01:00",
  "ThuStop": "2005-08-22T04:22:27.0486609+02:00",
  "FriStart": "2024-05-24T04:22:27.0486609+02:00",
  "FriStop": "1999-12-18T04:22:27.0486609+01:00",
  "SatStart": "2008-04-30T04:22:27.0486609+02:00",
  "SatStop": "2003-09-24T04:22:27.0486609+02:00",
  "SunStart": "2023-07-31T04:22:27.0486609+02:00",
  "SunStop": "2014-04-25T04:22:27.0486609+02:00",
  "NonDates": [
    "quibusdam",
    "numquam"
  ],
  "EscalationLevels": [
    {
      "TicketAlertId": 757,
      "AlertLevel": 170,
      "AlertTimeout": 766,
      "Action": 797,
      "DelegateTo": 491,
      "ScriptId": 886,
      "EmailTo": "kenya_kuhn@dicki.com",
      "SmsTo": "ea",
      "ReplyTemplateIdCustomer": 726,
      "ReplyTemplateIdUser": 824,
      "ReplyTemplateIdCatmast": 988,
      "ReplyTemplateIdEmail": 460,
      "RtiCustomerSms": 538,
      "ReplyTemplateIdUserSms": 208,
      "ReplyTemplateIdCatmastSms": 503,
      "ReplyTemplateIdSms": 76,
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 577
        }
      }
    }
  ],
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 506
    }
  }
}
```