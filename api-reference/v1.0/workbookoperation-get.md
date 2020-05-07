---
title: "Get workbookOperation"
description: "Retrieve the properties and relationships of workbookOperation object."
localization_priority: Normal
author: "grangeryy"
ms.prod: "excel"
doc_type: "apiPageType"
---

# Get workbookOperation

Retrieve the properties and relationships of workbookOperation object. This applies to operations that return the **Operation-Location** header in the response.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

| Permission type                        | Permissions (from least to most privileged) |
|:---------------------------------------|:--------------------------------------------|
| Delegated (work or school account)     | Files.ReadWrite. |
| Delegated (personal Microsoft account) | Not supported. |
| Application                            | Not supported. |

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
GET workbook/operations/{operation-id}
```

## Request headers

| Name      |Description|
|:----------|:----------|
| Authorization | Bearer {token}. Required. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and the requested [workbookOperation](../resources/workbookoperation.md) object in the response body.

## Examples

Here is the case of long running operation for creating a session.

### Request

The following is an example of the request.
<!-- {
  "blockType": "request",
  "name": "get_workbookoperation"
}-->

```http
GET https://graph.microsoft.com/v1.0/me/drive/items/{drive-item-id}/workbook/operations/{operation-id}
```

### Response

Here is the example of the response with the status of "running".


<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.workbookOperation"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "operation-id",
  "status": "running",
}
```

Here is the example fo response with the status of "succeeded".

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "operation-id",
  "status": "succeeded",
  "resourceLocation":"https://graph.microsoft.com/v1.0/me/drive/items/{drive-item-id}/workbook/sessionInfoResource(key='{key}')"
}
```

Here is the example of response with the status of "failed".

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "operation-id",
  "status": "failed",
  "error":
  {
      "code": "UnsupportedFeatureEditWarning",
      "message": "The workbook contains unsupported features and therefore cannot be edited."
  }
}
```

<!-- uuid: 16cd6b66-4b1a-43a1-adaf-3a886856ed98
2019-02-04 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get workbookOperation",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
