---
title: POST Agents/List/GetListItemsForHeading
uid: v1ListAgent_GetListItemsForHeading
generated: true
---

# POST Agents/List/GetListItemsForHeading

```http
POST /api/v1/Agents/List/GetListItemsForHeading
```

List of list items that is selected if under this heading







## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category". Default = show all fields. |

```http
POST /api/v1/Agents/List/GetListItemsForHeading?$select=name,department,category/id
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

UdListDefinitionId, HeadingId 

| Property Name | Type |  Description |
|----------------|------|--------------|
| UdListDefinitionId | Integer |  |
| HeadingId | Integer |  |

## Response:array

OK

| Response | Description |
|----------------|-------------|
| 200 | OK |

### Response body: array

| Property Name | Type |  Description |
|----------------|------|--------------|
| Id | int32 | The Id of the ListItem |
| Name | string | The name of the ListItem |
| ToolTip | string | The tooltip of the ListItem |
| Deleted | bool | The deleted status of the ListItem |
| Rank | int32 | The rank of the ListItem |
| Type | string | The type of the ListItem. Custom field. |
| ColorBlock | int32 | The color indicator of the ListItem color block |
| IconHint | string | The Icon hint of the ListItem. Custom field. |
| Selected | bool | True if the ListItem is selected |
| LastChanged | date-time | Time of last change. |
| ChildItems | array | The child items of the SelectableMDOListItem |
| ExtraInfo | string | Extra information added to the ListItem. Could be information such as sort order etc or other meta data. Custom field. |
| StyleHint | string | Style hint indicating, information such as background color etc. Custom field. |
| Hidden | bool | True if the ListItem is hidden |
| FullName | string | The name of the ListItem in its context |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |

## Sample request

```http!
POST /api/v1/Agents/List/GetListItemsForHeading
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: *
Content-Type: application/json; charset=utf-8

{
  "UdListDefinitionId": 411,
  "HeadingId": 567
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
  {
    "Id": 97,
    "Name": "Predovic Group",
    "ToolTip": "Et odit tempore sunt repudiandae culpa perspiciatis temporibus.",
    "Deleted": true,
    "Rank": 318,
    "Type": "et",
    "ColorBlock": 233,
    "IconHint": "libero",
    "Selected": false,
    "LastChanged": "2009-07-27T23:03:56.2271254+02:00",
    "ChildItems": [
      {
        "Id": 181,
        "Name": "Kuvalis-Lebsack",
        "ToolTip": "Quae facilis dolorem incidunt deserunt fugit unde dolorum.",
        "Deleted": true,
        "Rank": 877,
        "Type": "nostrum",
        "ColorBlock": 487,
        "IconHint": "velit",
        "Selected": true,
        "LastChanged": "2019-11-16T23:03:56.2276236+01:00",
        "ChildItems": [
          {},
          {}
        ],
        "ExtraInfo": "ipsa",
        "StyleHint": "itaque",
        "Hidden": false,
        "FullName": "Francisca Tillman",
        "TableRight": null,
        "FieldProperties": {
          "fieldName": {
            "FieldRight": null,
            "FieldType": "System.Int32",
            "FieldLength": 913
          }
        }
      }
    ],
    "ExtraInfo": "quia",
    "StyleHint": "et",
    "Hidden": false,
    "FullName": "Kristian Langosh",
    "TableRight": null,
    "FieldProperties": {
      "fieldName": {
        "FieldRight": null,
        "FieldType": "System.String",
        "FieldLength": 508
      }
    }
  }
]
```