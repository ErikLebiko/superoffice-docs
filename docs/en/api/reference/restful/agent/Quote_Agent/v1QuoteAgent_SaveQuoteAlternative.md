---
title: POST Agents/Quote/SaveQuoteAlternative
uid: v1QuoteAgent_SaveQuoteAlternative
generated: true
---

# POST Agents/Quote/SaveQuoteAlternative

```http
POST /api/v1/Agents/Quote/SaveQuoteAlternative
```

Updates the existing QuoteAlternative or creates a new QuoteAlternative if the id parameter is empty








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

The QuoteAlternative to be saved. 

| Property Name | Type |  Description |
|----------------|------|--------------|
| QuoteAlternativeId | Integer | Primary key |
| ERPQuoteAlternativeKey | String | Key that identifies this alternative in the ERP system, if it exists there. |
| QuoteVersionId | Integer | The version that owns this alternative (the chain is Sale 1-&gt;1 Quote 1-&gt;+ QuoteVersion 1-&gt;+ QuoteAlternative. |
| Name | String | Name of Alternative. Shown in tab in user interface, intentionally kept short |
| Description | String | The tool-tip to use in the user interface (on the tab, for instance). |
| Status | String | If there was a problem with for instance calculation, this field is set to warning or error. |
| Reason | String | If there was a problem, this field contains a localized explanation of the problem and possible steps to fix it that the user can be shown. |
| ERPDiscountPercent | Number | The discount the system calculates based on customer /amount / whatever. Can be overridden by the sales rep in the field ‘DiscountPercent’ or ‘DiscountAmount’. Both the two ‘ERPDiscountPercent’ and ‘ERPDiscountAmount’ shall be filled out. If UserValueOverride is 'None', then the ERPDiscountAmount shall be copied into DiscountAmount and ERPDiscountPercent into DiscountPercent. The Percentage is given in integer form, i.e. ‘12%’ is represented as ‘12’. |
| ERPDiscountAmount | Number | The discount the system calculates based on customer /amount / whatever. Can be overridden by the user in the field ‘DiscountPercent’ or ‘DiscountAmount’. Both the two ‘ERPDiscountPercent’ and ‘ERPDiscountAmount’ shall be filled out. If UserValueOverride is 'None', then the ERPDiscountAmount shall be copied into DiscountAmount and ERPDiscountPercent into DiscountPercent. |
| DiscountPercent | Number | The discount the sales rep specifies, in percent. Both the two ‘DiscountPercent’ and ‘DiscountAmount’ shall be filled out, but the UserValueOverride field must be set to the field the user actually changed. If this field is filled out by the user, it overrides the discount suggested by the connector. If the user has not filled any values, the system will copy the ERP discount percent value into this field. The Percentage is given in integer form, i.e. ‘12%’ is represented as ‘12’. |
| DiscountAmount | Number | The discount the sales rep specifies, in whatever currency the sale is in. Both the two ‘DiscountPercent’ and ‘DiscountAmount’ shall be filled out, but the UserValueOverride field must be set to the field the user actually changed. If this field is filled out by the user, it overrides the discount suggested by the connector. If the user has not filled any values, the system will copy the ERP discount amount value into this field. |
| UserValueOverride | String | Has the pre-calculated (from ERP) price information been overridden, and how. If the user has filled out the discountpercentage field, then the UserValueOverride field is set to OverridePercent. (The DiscountAmount, EarningPercent, EarningAmount and TotalPrice fields are calculated based on the discountPercent.) |
| VATInfo | String | Extra info about VAT that the connector might insert. This field has no business logic in the CRM code, but is available as a merge field in the quote documents. |
| VAT | Number | Tax/VAT - THIS IS AN AMOUNT, available as a merge field in the quote document. The SuperOffice quote connector will calculate this field based on the vat PERCENTAGES on the individual lines; other connectors may implement other algorithms at will. |
| EarningPercent | Number | The earning on this alternative, in percent of total. The Percentage is given in integer form, i.e. ‘12%’ is represented as ‘12’. |
| EarningAmount | Number | Earning on this alternative, as an absolute amount |
| SubTotal | Number | Value to help the user interface, is computed by summing the totalprice of the quotelines, and NOT by summing their subtotals |
| TotalPrice | Number | Sum of the QuoteLines.TotalPrice - AlternativeDiscount or QuoteLines.TotalCost + Earning based on what, if anything, the user has entered last. Shall be calculated by the connector. |
| ExtraField1 | String | Optional information added by Quote Connector; usable in the quote document merge process |
| ExtraField2 | String | Optional information added by Quote Connector; usable in the quote document merge process |
| ExtraField3 | String | Optional information added by Quote Connector; usable in the quote document merge process |
| ExtraField4 | String | Optional information added by Quote Connector; usable in the quote document merge process |
| ExtraField5 | String | Optional information added by Quote Connector; usable in the quote document merge process |

## Response:

OK

| Response | Description |
|----------------|-------------|
| 200 | OK |

### Response body: QuoteAlternative

| Property Name | Type |  Description |
|----------------|------|--------------|
| QuoteAlternativeId | int32 | Primary key |
| ERPQuoteAlternativeKey | string | Key that identifies this alternative in the ERP system, if it exists there. |
| QuoteVersionId | int32 | The version that owns this alternative (the chain is Sale 1-&gt;1 Quote 1-&gt;+ QuoteVersion 1-&gt;+ QuoteAlternative. |
| Name | string | Name of Alternative. Shown in tab in user interface, intentionally kept short |
| Description | string | The tool-tip to use in the user interface (on the tab, for instance). |
| Status | string | If there was a problem with for instance calculation, this field is set to warning or error. |
| Reason | string | If there was a problem, this field contains a localized explanation of the problem and possible steps to fix it that the user can be shown. |
| ERPDiscountPercent | double | The discount the system calculates based on customer /amount / whatever. Can be overridden by the sales rep in the field ‘DiscountPercent’ or ‘DiscountAmount’. Both the two ‘ERPDiscountPercent’ and ‘ERPDiscountAmount’ shall be filled out. If UserValueOverride is 'None', then the ERPDiscountAmount shall be copied into DiscountAmount and ERPDiscountPercent into DiscountPercent. The Percentage is given in integer form, i.e. ‘12%’ is represented as ‘12’. |
| ERPDiscountAmount | double | The discount the system calculates based on customer /amount / whatever. Can be overridden by the user in the field ‘DiscountPercent’ or ‘DiscountAmount’. Both the two ‘ERPDiscountPercent’ and ‘ERPDiscountAmount’ shall be filled out. If UserValueOverride is 'None', then the ERPDiscountAmount shall be copied into DiscountAmount and ERPDiscountPercent into DiscountPercent. |
| DiscountPercent | double | The discount the sales rep specifies, in percent. Both the two ‘DiscountPercent’ and ‘DiscountAmount’ shall be filled out, but the UserValueOverride field must be set to the field the user actually changed. If this field is filled out by the user, it overrides the discount suggested by the connector. If the user has not filled any values, the system will copy the ERP discount percent value into this field. The Percentage is given in integer form, i.e. ‘12%’ is represented as ‘12’. |
| DiscountAmount | double | The discount the sales rep specifies, in whatever currency the sale is in. Both the two ‘DiscountPercent’ and ‘DiscountAmount’ shall be filled out, but the UserValueOverride field must be set to the field the user actually changed. If this field is filled out by the user, it overrides the discount suggested by the connector. If the user has not filled any values, the system will copy the ERP discount amount value into this field. |
| UserValueOverride | string | Has the pre-calculated (from ERP) price information been overridden, and how. If the user has filled out the discountpercentage field, then the UserValueOverride field is set to OverridePercent. (The DiscountAmount, EarningPercent, EarningAmount and TotalPrice fields are calculated based on the discountPercent.) |
| VATInfo | string | Extra info about VAT that the connector might insert. This field has no business logic in the CRM code, but is available as a merge field in the quote documents. |
| VAT | double | Tax/VAT - THIS IS AN AMOUNT, available as a merge field in the quote document. The SuperOffice quote connector will calculate this field based on the vat PERCENTAGES on the individual lines; other connectors may implement other algorithms at will. |
| EarningPercent | double | The earning on this alternative, in percent of total. The Percentage is given in integer form, i.e. ‘12%’ is represented as ‘12’. |
| EarningAmount | double | Earning on this alternative, as an absolute amount |
| SubTotal | double | Value to help the user interface, is computed by summing the totalprice of the quotelines, and NOT by summing their subtotals |
| TotalPrice | double | Sum of the QuoteLines.TotalPrice - AlternativeDiscount or QuoteLines.TotalCost + Earning based on what, if anything, the user has entered last. Shall be calculated by the connector. |
| ExtraField1 | string | Optional information added by Quote Connector; usable in the quote document merge process |
| ExtraField2 | string | Optional information added by Quote Connector; usable in the quote document merge process |
| ExtraField3 | string | Optional information added by Quote Connector; usable in the quote document merge process |
| ExtraField4 | string | Optional information added by Quote Connector; usable in the quote document merge process |
| ExtraField5 | string | Optional information added by Quote Connector; usable in the quote document merge process |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |

## Sample request

```http!
POST /api/v1/Agents/Quote/SaveQuoteAlternative
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: en
Content-Type: application/json; charset=utf-8

{
  "QuoteAlternativeId": 948,
  "ERPQuoteAlternativeKey": "dignissimos",
  "QuoteVersionId": 319,
  "Name": "Weimann, Barrows and Dickens",
  "Description": "Face to face background Graphical User Interface",
  "Status": "Error",
  "Reason": "",
  "ERPDiscountPercent": 29418.858,
  "ERPDiscountAmount": 10925.124,
  "DiscountPercent": 22693.293999999998,
  "DiscountAmount": 22461.378,
  "UserValueOverride": "DiscountAmount",
  "VATInfo": "consequatur",
  "VAT": 23094.446,
  "EarningPercent": 6430.968,
  "EarningAmount": 1661.02,
  "SubTotal": 11996.952,
  "TotalPrice": 12996.698,
  "ExtraField1": "magni",
  "ExtraField2": "minima",
  "ExtraField3": "aut",
  "ExtraField4": "velit",
  "ExtraField5": "asperiores"
}
```

## Sample response

```http_
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "QuoteAlternativeId": 276,
  "ERPQuoteAlternativeKey": "officiis",
  "QuoteVersionId": 374,
  "Name": "Thiel Inc and Sons",
  "Description": "Reverse-engineered bifurcated system engine",
  "Status": "Error",
  "Reason": "maximize real-time models",
  "ERPDiscountPercent": 8261.224,
  "ERPDiscountAmount": 26880.318,
  "DiscountPercent": 18954.432,
  "DiscountAmount": 16093.09,
  "UserValueOverride": "DiscountAmount",
  "VATInfo": "ipsum",
  "VAT": 5625.53,
  "EarningPercent": 7355.498,
  "EarningAmount": 30719.468,
  "SubTotal": 25379.131999999998,
  "TotalPrice": 25238.102,
  "ExtraField1": "recusandae",
  "ExtraField2": "voluptas",
  "ExtraField3": "ad",
  "ExtraField4": "nihil",
  "ExtraField5": "ad",
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.String",
      "FieldLength": 869
    }
  }
}
```