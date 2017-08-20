---
title: "CustomParameter Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d245d96-739c-4bad-b3b5-9cbbc95ec40e
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CustomParameter Data Object
Defines a key and value custom parameter for URL tracking. Used for campaign, ad group, ad, keyword, sitelink, and ad group criterion URL custom parameters.

## Syntax

```xml
\<xs:complexType name="CustomParameter">
  \<xs:sequence>
    \<xs:element name="Key" nillable="true" type="xs:string"/>
    \<xs:element name="Value" nillable="true" type="xs:string"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Key*|The name of the custom parameter that you want to track.<br /><br />**Note:** The maximum length of this string is 16, in UTF-8 bytes. With the Campaign Management service you may not specify special characters such as braces and underscore: \"\{\", \"\_\", and \"\}\".  With the Bulk service the surrounding braces and underscore are required. The maximum length of 16 UTF-8 bytes does not include the optional braces and underscore: \"\{\", \"\_\", and \"\}\".<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*Value*|The value to track using your custom parameter.<br /><br />The maximum length of this string is 200, in UTF-8 bytes.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also

[CustomParameters](../campaign-api/customparameters-data-object.md)  

