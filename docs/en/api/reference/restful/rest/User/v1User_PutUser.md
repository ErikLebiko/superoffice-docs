---
title: PUT User/{id}
uid: v1User_PutUser
generated: true
---

# PUT User/{id}

```http
PUT /api/v1/User/{id}
```

Updates the existing User


## Online Restricted: ## The User agent is not available in Online by default. User management is not allowed for partner apps.





| Path Part | Type | Description |
|-----------|------|-------------|
| id | int32 | The User id to update. **Required** |


## Query String Parameters

| Parameter Name | Type |  Description |
|----------------|------|--------------|
| $select | string |  Optional comma separated list of properties to include in the result. Other fields are then nulled out to reduce payload size: "Name,department,category" Default = show all fields. |

```http
PUT /api/v1/User/{id}?$select=name,department,category/id
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

## Request Body: entity 

The User to be saved. 

| Property Name | Type |  Description |
|----------------|------|--------------|
| AssociateId | Integer | Primary key |
| Name | String | Initials, UserId - also used as login name for on-site installations. Identifies user in archives. |
| Rank | Integer | Rank order |
| Tooltip | String | Tooltip or other description |
| LicenseOwners | Array | The restricted and unrestricted module licenses grouped by license owner. These module licenses are either assigned or unassigned to this user |
| Role | Role | Users role for role-based security. Determines permissions and access rights for the user. |
| UserGroup | UserGroup | The main user group that this user belongs to.  <para>Use MDO List name "usergroup" to get list items.</para> |
| OtherGroups | Array | The other groups this user is a member of, apart from the main user group.  <para>Use MDO List name "usergroup" to get list items.</para> |
| Person | Person | The person associated with this user. Detailed information about the user  <para>Use MDO List name "person_new" to get list items.</para> |
| Deleted | Boolean | If true, the user is retired and should have no rights, not appear in lists, etc. |
| Lastlogin | String | Last login date |
| Lastlogout | String | Last logout date |
| EjUserId | Integer | ID of the ej user record corresponding to this associate; 0 for associates that are not ej users |
| RequestSignature | String | ej users request signature |
| Type | String | User type: 1=InternalAssociate, 2=ResourceAssociate, 3=ExternalAssociate, 4=AnonymousAssociate, 5=SystemAssociate |
| IsPersonRetired | Boolean | True if the user is retired and should have no rights, not appear in lists, etc. |
| IsOnTravel | Boolean | True if the user is on travel. |
| Credentials | Array | List of credentials registered for this user. i.e. valid authentication methods. |
| UserName | String | User name, a.k.a. Login name. This might be an e-mail address. |
| TicketCategories | Array | Request Ticket Categories assigned to the user.   <para>Use MDO List name "ejCategory" to get list items.</para> |
| NickName | String | The unique nick name for this user. Used in Service as an alias, similar to Name/Initials. |
| WaitingForApproval | Boolean | The user is waiting for an administrator to approve/grant her/him access. |
| ExtraFields | Object | Deprecated: Use {SuperOffice.CRM.Services.User.CustomFields} instead. Extra fields added to the carrier. This could be data from Plug-ins, the foreign key system, external applications, etc. |
| CustomFields | Object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.User.ExtraFields} and <see cref="!:UserDefinedFields">UserDefinedFields</see> properties are deprecated in favor of this combined collection. |
| PostSaveCommands | Array | Post custom commands the client should execute after save has completed. |

## Response:

User updated.

| Response | Description |
|----------------|-------------|
| 200 | User updated. |
| 400 | Bad request. Entity to save is not in request body. |

### Response body: UserWithLinks

| Property Name | Type |  Description |
|----------------|------|--------------|
| AssociateId | int32 | Primary key |
| Name | string | Initials, UserId - also used as login name for on-site installations. Identifies user in archives. |
| Rank | int32 | Rank order |
| Tooltip | string | Tooltip or other description |
| LicenseOwners | array | The restricted and unrestricted module licenses grouped by license owner. These module licenses are either assigned or unassigned to this user |
| Role | Role | Users role for role-based security. Determines permissions and access rights for the user. |
| UserGroup | UserGroup | The main user group that this user belongs to.  Use MDO List name "usergroup" to get list items. |
| OtherGroups | array | The other groups this user is a member of, apart from the main user group.  Use MDO List name "usergroup" to get list items. |
| Person | Person | The person associated with this user. Detailed information about the user  Use MDO List name "person_new" to get list items. |
| Deleted | bool | If true, the user is retired and should have no rights, not appear in lists, etc. |
| Lastlogin | date-time | Last login date |
| Lastlogout | date-time | Last logout date |
| EjUserId | int32 | ID of the ej user record corresponding to this associate; 0 for associates that are not ej users |
| RequestSignature | string | ej users request signature |
| Type | string | User type: 1=InternalAssociate, 2=ResourceAssociate, 3=ExternalAssociate, 4=AnonymousAssociate, 5=SystemAssociate |
| IsPersonRetired | bool | True if the user is retired and should have no rights, not appear in lists, etc. |
| IsOnTravel | bool | True if the user is on travel. |
| Credentials | array | List of credentials registered for this user. i.e. valid authentication methods. |
| UserName | string | User name, a.k.a. Login name. This might be an e-mail address. |
| TicketCategories | array | Request Ticket Categories assigned to the user.   Use MDO List name "ejCategory" to get list items. |
| NickName | string | The unique nick name for this user. Used in Service as an alias, similar to Name/Initials. |
| WaitingForApproval | bool | The user is waiting for an administrator to approve/grant her/him access. |
| ExtraFields | object | Deprecated: Use {SuperOffice.CRM.Services.User.CustomFields} instead. Extra fields added to the carrier. This could be data from Plug-ins, the foreign key system, external applications, etc. |
| CustomFields | object | Udef + Extra fields added to the carrier. Extra fields as defined by changes to database schema + user-defined fields as defined by admin. Custom fields combines user defined fields and extra fields into one bucket.  The individual {SuperOffice.CRM.Services.User.ExtraFields} and UserDefinedFields properties are deprecated in favor of this combined collection. |
| PostSaveCommands | array | Post custom commands the client should execute after save has completed. |
| TableRight | TableRight | The carrier's table right |
| FieldProperties | object | Field property dictionary mapping field names to field access rights. |
| _Links | object |  |

## Sample request

```http!
PUT /api/v1/User/{id}
Authorization: Basic dGplMDpUamUw
Accept: application/json; charset=utf-8
Accept-Language: sv
Content-Type: application/json; charset=utf-8

{
  "AssociateId": 225,
  "Name": "Strosin-Kshlerin",
  "Rank": 37,
  "Tooltip": "accusantium",
  "LicenseOwners": [
    {
      "Name": "Cronin, White and Funk",
      "Description": "Business-focused interactive solution",
      "RestrictedModuleLicenses": [
        {},
        {}
      ],
      "UnrestrictedModuleLicenses": [
        {},
        {}
      ]
    },
    {
      "Name": "Cronin, White and Funk",
      "Description": "Business-focused interactive solution",
      "RestrictedModuleLicenses": [
        {},
        {}
      ],
      "UnrestrictedModuleLicenses": [
        {},
        {}
      ]
    }
  ],
  "Role": null,
  "UserGroup": null,
  "OtherGroups": [
    {
      "Value": "deleniti",
      "Tooltip": "est",
      "Id": 762,
      "Rank": 544,
      "Deleted": true
    },
    {
      "Value": "deleniti",
      "Tooltip": "est",
      "Id": 762,
      "Rank": 544,
      "Deleted": true
    }
  ],
  "Person": null,
  "Deleted": true,
  "Lastlogin": "2008-09-04T04:02:07.009732+02:00",
  "Lastlogout": "2024-01-19T04:02:07.009732+01:00",
  "EjUserId": 589,
  "RequestSignature": "vero",
  "Type": "AnonymousAssociate",
  "IsPersonRetired": false,
  "IsOnTravel": false,
  "Credentials": [
    {
      "Type": null,
      "Value": "voluptatem",
      "DisplayValue": "odio"
    },
    {
      "Type": null,
      "Value": "voluptatem",
      "DisplayValue": "odio"
    }
  ],
  "UserName": "Weimann Inc and Sons",
  "TicketCategories": [
    {
      "Id": 213,
      "Name": "Hills-Jacobson",
      "ToolTip": "Ex voluptatem dolorem distinctio voluptatem voluptas cumque doloremque.",
      "Deleted": false,
      "Rank": 671,
      "Type": "eius",
      "ChildItems": [
        {},
        {}
      ],
      "IconHint": "ullam",
      "ColorBlock": 296,
      "ExtraInfo": "eveniet",
      "StyleHint": "excepturi",
      "FullName": "Miss Lonny Corrine Erdman"
    }
  ],
  "NickName": "Wolf, Hermiston and Schneider",
  "WaitingForApproval": false,
  "ExtraFields": {
    "ExtraFields1": "dignissimos",
    "ExtraFields2": "ab"
  },
  "CustomFields": {
    "CustomFields1": "dolorem",
    "CustomFields2": "amet"
  },
  "PostSaveCommands": [
    {
      "Name": "Blanda, Yost and Murphy",
      "DisplayName": "Grady-Gibson",
      "Description": "Upgradable 24 hour solution",
      "ToolTip": "Et saepe quibusdam rem odio nesciunt.",
      "Actions": "Implicit",
      "ActionData": "suscipit"
    },
    {
      "Name": "Blanda, Yost and Murphy",
      "DisplayName": "Grady-Gibson",
      "Description": "Upgradable 24 hour solution",
      "ToolTip": "Et saepe quibusdam rem odio nesciunt.",
      "Actions": "Implicit",
      "ActionData": "suscipit"
    }
  ]
}
```

## Sample response

```http_
HTTP/1.1 200 User updated.
Content-Type: application/json; charset=utf-8

{
  "AssociateId": 529,
  "Name": "Hirthe Group",
  "Rank": 464,
  "Tooltip": "laudantium",
  "LicenseOwners": [
    {
      "Name": "Cruickshank, Fritsch and Langosh",
      "Description": "Implemented tertiary monitoring",
      "RestrictedModuleLicenses": [
        {},
        {}
      ],
      "UnrestrictedModuleLicenses": [
        {},
        {}
      ],
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 977
        }
      }
    },
    {
      "Name": "Cruickshank, Fritsch and Langosh",
      "Description": "Implemented tertiary monitoring",
      "RestrictedModuleLicenses": [
        {},
        {}
      ],
      "UnrestrictedModuleLicenses": [
        {},
        {}
      ],
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 977
        }
      }
    }
  ],
  "Role": null,
  "UserGroup": null,
  "OtherGroups": [
    {
      "Value": "sed",
      "Tooltip": "est",
      "Id": 428,
      "Rank": 260,
      "Deleted": false,
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 817
        }
      }
    }
  ],
  "Person": null,
  "Deleted": false,
  "Lastlogin": "2003-02-11T04:02:07.0253551+01:00",
  "Lastlogout": "2003-06-06T04:02:07.0253551+02:00",
  "EjUserId": 865,
  "RequestSignature": "autem",
  "Type": "AnonymousAssociate",
  "IsPersonRetired": false,
  "IsOnTravel": false,
  "Credentials": [
    {
      "Type": null,
      "Value": "maxime",
      "DisplayValue": "officiis",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 275
        }
      }
    },
    {
      "Type": null,
      "Value": "maxime",
      "DisplayValue": "officiis",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 275
        }
      }
    }
  ],
  "UserName": "Larkin Inc and Sons",
  "TicketCategories": [
    {
      "Id": 703,
      "Name": "Adams, McDermott and Hackett",
      "ToolTip": "Nisi assumenda qui corrupti possimus ducimus.",
      "Deleted": false,
      "Rank": 387,
      "Type": "enim",
      "ChildItems": [
        {},
        {}
      ],
      "IconHint": "quos",
      "ColorBlock": 81,
      "ExtraInfo": "pariatur",
      "StyleHint": "ipsum",
      "FullName": "Ms. Rudolph Minnie Schroeder",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.Int32",
          "FieldLength": 424
        }
      }
    }
  ],
  "NickName": "Auer-Bruen",
  "WaitingForApproval": false,
  "ExtraFields": {
    "ExtraFields1": "in",
    "ExtraFields2": "ullam"
  },
  "CustomFields": {
    "CustomFields1": "sed",
    "CustomFields2": "quam"
  },
  "PostSaveCommands": [
    {
      "Name": "Herzog-Turcotte",
      "DisplayName": "Brakus Group",
      "Description": "Implemented composite success",
      "ToolTip": "Optio dolores.",
      "Actions": "Implicit",
      "ActionData": "labore",
      "TableRight": null,
      "FieldProperties": {
        "fieldName": {
          "FieldRight": null,
          "FieldType": "System.String",
          "FieldLength": 524
        }
      }
    }
  ],
  "TableRight": null,
  "FieldProperties": {
    "fieldName": {
      "FieldRight": null,
      "FieldType": "System.Int32",
      "FieldLength": 3
    }
  },
  "_Links": {
    "Self": "https://www.example.com/api/v1/project/321",
    "Archive": "https://www.example.com/api/v1/project"
  }
}
```