---
title: "userDataSecurityAndGovernance: processContent"
toc.title: "userDataSecurityAndGovernance: processContent"
description: "Process content against data protection policies in the context of the current user."
author: "ArunGedela"
ms.date: 04/08/2025
ms.localizationpriority: medium
ms.subservice: "security"
doc_type: apiPageType
---

# userDataSecurityAndGovernance: processContent

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Process content against data protection policies in the context of the current user. 

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "userdatasecurityandgovernance-processcontent-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/userdatasecurityandgovernance-processcontent-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /me/dataSecurityAndGovernance/processContent
POST /users/{usersId}/dataSecurityAndGovernance/processContent
```

/me/dataSecurityAndGovernance/processContent supports delegated permissions only.

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|
| If-None-Match | Optional. This value is used by the API to determine if the policy state changed since the last call to the API. The value is from the Etag header returned from [protectionScopes compute](../api/userprotectionscopecontainer-compute.md)|

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

|Parameter|Type|Description|
|:---|:---|:---|
|contentToProcess|[processContentRequest](../resources/processcontentrequest.md)|Required. The object containing the content entries and metadata (activity, device, application) to be evaluated for the specified user.|

## Response headers

| Name          | Description   |
| :------------ | :------------ |
| ETag          | An indicator whether the configured policy state changed. If the policy state changed, the protectionScopeState property returned will be "modified" and the app needs to refresh by calling [protectionScopes compute](../api/userprotectionscopecontainer-compute.md). |

## Response

If successful, this action returns a `200 OK` response code and a [processContentResponse](../resources/processcontentresponse.md) in the response body.

## Examples

### Example 1: Enterprise AI app

#### Request

The following example shows a request.
# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "userdatasecurityandgovernance.processcontent_1"
}
-->
``` http
POST https://graph.microsoft.com/beta/me/dataSecurityAndGovernance/processContent
Content-Type: application/json

{
    "contentToProcess": {
       "contentEntries": [
          {
             "@odata.type": "microsoft.graph.processConversationMetadata",
             "identifier": "07785517-9081-4fe7-a9dc-85bcdf5e9075",
             "content": {
                "@odata.type": "microsoft.graph.textContent", 
                "data": "Write an acceptance letter for Alex Wilber with Credit card number 4532667785213500, ssn: 120-98-1437 at One Microsoft Way, Redmond, WA 98052"
             },
             "name":"PC Purview API Explorer message",
             "correlationId": "d63eafd2-e3a9-4c1a-b726-a2e9b9d9580d",
             "sequenceNumber": 0, 
             "isTruncated": false,
             "createdDateTime": "2025-05-27T17:23:20",
             "modifiedDateTime": "2025-05-27T17:23:20"
          }
       ],
       "activityMetadata": { 
          "activity": "uploadText"
       },
       "deviceMetadata": {
          "operatingSystemSpecifications": {
             "operatingSystemPlatform": "Windows 11",
             "operatingSystemVersion": "10.0.26100.0" 
          },
          "ipAddress": "127.0.0.1"
       },
       "protectedAppMetadata": {
          "name": "PC Purview API Explorer",
          "version": "0.2",
          "applicationLocation":{
             "@odata.type": "microsoft.graph.policyLocationApplication",
             "value": "83ef208a-0396-4893-9d4f-d36efbffc8bd"
          }
       },
       "integratedAppMetadata": {
          "name": "PC Purview API Explorer",
          "version": "0.2" 
       }
    }
}
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/userdatasecurityandgovernanceprocesscontent-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/userdatasecurityandgovernanceprocesscontent-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/userdatasecurityandgovernanceprocesscontent-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/userdatasecurityandgovernanceprocesscontent-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/userdatasecurityandgovernanceprocesscontent-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/userdatasecurityandgovernanceprocesscontent-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/userdatasecurityandgovernanceprocesscontent-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.processContentResponse"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.processContentResponse",
  "protectionScopeState": "notModified",
  "policyActions": [],
  "processingErrors": []
}
```

### Example 2: Network provider app 

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "userdatasecurityandgovernance.processcontent_2"
}
-->
``` http
POST https://graph.microsoft.com/beta/me/dataSecurityAndGovernance/processContent
Content-Type: application/json

{
    "contentToProcess": {
        "contentEntries": [
            {
                "@odata.type": "#microsoft.graph.processConversationMetadata",
                "identifier": "f7af180f-dc2e-467c-9719-757e1c61eabf",
                "content": {
                    "@odata.type": "#microsoft.graph.textContent",
                    "data": "some data"
                },
                "name": "Some name",
             "correlationId": "d63eafd2-e3a9-4c1a-b726-a2e9b9d95811",
             "sequenceNumber": 0, 
            }
        ],
        "activityMetadata": {
            "activity": "uploadText"
        },
        "deviceMetadata": {
            "deviceType": "Unmanaged",
            "ipAddress": null,
            "operatingSystemSpecifications": {
                "operatingSystemPlatform": "Windows",
                "operatingSystemVersion": "11.1"
            }
        },
        "integratedAppMetadata": {
            "name": "Some integrated app name",
            "version": "1.0.0"
        },
        "protectedAppMetadata": {
            "applicationLocation": {
                "@odata.type": "#microsoft.graph.policyLocationUrl",
                "value": "https://gemini.google.com"
            }
        }
    }
} 

```

#### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.processContentResponse"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.processContentResponse",
  "protectionScopeState": "modified",
  "policyActions": [
    {
      "@odata.type": "#microsoft.graph.restrictAccessAction",
      "action": "restrictAccess",
      "restrictionAction": "block"
    }
  ],
  "processingErrors": []
}
```

### Example 3: Network provider app with file content

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "userdatasecurityandgovernance.processcontent_3"
}
-->
``` http
POST https://graph.microsoft.com/beta/me/dataSecurityAndGovernance/processContent
Content-Type: application/json

{
    "contentToProcess": {
        "contentEntries": [
            {
                "@odata.type": "#microsoft.graph.processConversationMetadata",
                "identifier": "f7af180f-dc2e-467c-9719-757e1c61eabf",
                "content": {
                    "@odata.type": "#microsoft.graph.binaryContent",
                    "data": "Base64 encoded content"
                },
                "name": "Some name",
                "correlationId": "d63eafd2-e3a9-4c1a-b726-a2e9b9d95822"
            }
        ],
        "activityMetadata": {
            "activity": "uploadFile"
        },
        "deviceMetadata": {
            "deviceType": "Unmanaged",
            "ipAddress": null,
            "operatingSystemSpecifications": {
                "operatingSystemPlatform": "Windows",
                "operatingSystemVersion": "11.1"
            }
        },
        "integratedAppMetadata": {
            "name": "Some integrated app name",
            "version": "1.0.0"
        },
        "protectedAppMetadata": {
            "applicationLocation": {
                "@odata.type": "#microsoft.graph.policyLocationUrl",
                "value": "https://gemini.google.com"
            }
        }
    }
}
```

#### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.processContentResponse"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.processContentResponse",
  "protectionScopeState": "modified",
  "policyActions": [
    {
      "@odata.type": "#microsoft.graph.restrictAccessAction",
      "action": "restrictAccess",
      "restrictionAction": "block"
    }
  ],
  "processingErrors": []
}
```
