---
title: POST Dashboard
uid: v1Dashboard_PostDashboard
generated: true
---

# POST Dashboard

```http
POST /api/v1/Dashboard
```

Creates a new Dashboard


Calls the Dashboard agent service SaveDashboard.






## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category" Default = show all fields. |

```http
POST /api/v1/Dashboard?$select=name,department,category/id
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

The Dashboard to be saved. 

| Property Name | Type |  Description |
|----------------|------|--------------|
| DashboardId | Integer | The dashboard id |
| AssociateId | Integer | Id of the associate who owns this dashboard |
| Caption | String | The caption for this dashboard |
| Layout | String | The dashboard layout, how the tiles are organized on the screen |
| Tiles | Array | The tiles associated with this dashboard |

## Response:

OK

| Response | Description |
|----------------|-------------|
| 200 | OK |

### Response body: DashboardWithLinks

| Property Name | Type |  Description |
|----------------|------|--------------|
| DashboardId | int32 | The dashboard id |
| AssociateId | int32 | Id of the associate who owns this dashboard |
| Caption | string | The caption for this dashboard |
| Layout | string | The dashboard layout, how the tiles are organized on the screen |
| Tiles | array | The tiles associated with this dashboard |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |
| _Links | object |  |

## Sample request

```http!
POST /api/v1/Dashboard
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: sv
Content-Type: application/json; charset=utf-8

{
  "DashboardId": 789,
  "AssociateId": 719,
  "Caption": "magnam",
  "Layout": "Four",
  "Tiles": [
    {
      "DashboardTileId": 420,
      "Caption": "illum",
      "Description": "Fundamental dedicated portal",
      "ChartName": "Hagenes, Stamm and Rohan",
      "ChartId": "laudantium",
      "IsDefault": false,
      "AssociateId": 27,
      "GroupId": 425,
      "SelectionId": 420,
      "Config": "voluptatem",
      "Type": "Bignum",
      "EntityType": "Activity",
      "Options": [
        {},
        {}
      ],
      "VisibleFor": [
        {},
        {}
      ]
    }
  ]
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "DashboardId": 35,
  "AssociateId": 765,
  "Caption": "itaque",
  "Layout": "Four",
  "Tiles": [
    {
      "DashboardTileId": 48,
      "Caption": "non",
      "Description": "Extended dynamic emulation",
      "ChartName": "Ledner, Nikolaus and Rempel",
      "ChartId": "nesciunt",
      "IsDefault": false,
      "AssociateId": 234,
      "GroupId": 483,
      "SelectionId": 171,
      "Config": "numquam",
      "Type": "Bignum",
      "EntityType": "Activity",
      "Options": [
        {},
        {}
      ],
      "VisibleFor": [
        {},
        {}
      ],
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 167
        }
      }
    }
  ],
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 760
    }
  },
  "_Links": {
    "Self": "https://www.example.com/api/v1/project/321",
    "Archive": "https://www.example.com/api/v1/project"
  }
}
```