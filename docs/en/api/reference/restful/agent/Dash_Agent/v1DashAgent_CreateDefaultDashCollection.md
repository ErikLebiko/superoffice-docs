---
title: POST Agents/Dash/CreateDefaultDashCollection
uid: v1DashAgent_CreateDefaultDashCollection
generated: true
---

# POST Agents/Dash/CreateDefaultDashCollection

```http
POST /api/v1/Agents/Dash/CreateDefaultDashCollection
```

Set default values into a new DashCollection.


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

### Response body: DashCollection

| Property Name | Type |  Description |
|----------------|------|--------------|
| Pinned | array | Dashboards pinned to the associate |
| Favourites | array | The assocates favourite dashboards |
| Other | array | Other dashboards |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |

## Sample request

```http!
POST /api/v1/Agents/Dash/CreateDefaultDashCollection
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: *
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "Pinned": [
    {
      "DashboardId": 80,
      "UniqueId": "ad",
      "Name": "Lang-Luettgen",
      "Description": "Expanded explicit parallelism",
      "AssociateId": 665,
      "Columns": 661,
      "Theme": null,
      "VisibleForAll": 604,
      "VisibleForAssociates": [
        689,
        29
      ],
      "VisibleForGroups": [
        384,
        736
      ],
      "PinForAll": 986,
      "PinForAssociates": [
        150,
        271
      ],
      "PinForGroups": [
        525,
        140
      ],
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 104
        }
      }
    }
  ],
  "Favourites": [
    {
      "DashboardId": 513,
      "UniqueId": "commodi",
      "Name": "Donnelly, Littel and Sanford",
      "Description": "Phased logistical instruction set",
      "AssociateId": 791,
      "Columns": 341,
      "Theme": null,
      "VisibleForAll": 30,
      "VisibleForAssociates": [
        718,
        383
      ],
      "VisibleForGroups": [
        916,
        172
      ],
      "PinForAll": 251,
      "PinForAssociates": [
        564,
        177
      ],
      "PinForGroups": [
        854,
        7
      ],
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 291
        }
      }
    }
  ],
  "Other": [
    {
      "DashboardId": 171,
      "UniqueId": "aut",
      "Name": "Witting, Walter and Watsica",
      "Description": "Diverse discrete task-force",
      "AssociateId": 663,
      "Columns": 167,
      "Theme": null,
      "VisibleForAll": 80,
      "VisibleForAssociates": [
        553,
        810
      ],
      "VisibleForGroups": [
        555,
        795
      ],
      "PinForAll": 746,
      "PinForAssociates": [
        7,
        962
      ],
      "PinForGroups": [
        445,
        562
      ],
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 621
        }
      }
    }
  ],
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 935
    }
  }
}
```