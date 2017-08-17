---
title: "CustomParameters Data Object"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 226b4a32-d560-4c9a-a2ff-6ab09c7586f8
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CustomParameters Data Object
Defines a collection of key and value custom parameters for URL tracking. Used for campaign, ad group, ad, keyword, sitelink, and ad group criterion URL custom parameters.

## Syntax

```xml
\<xs:complexType name="CustomParameters">
  \<xs:sequence>
    \<xs:element name="Parameters" nillable="true" type="tns:ArrayOfCustomParameter"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|`Parameters`|The collection of key and value custom parameters for URL tracking.<br /><br />You can have a maximum of 3 [CustomParameter](../campaign-api/customparameter-data-object.md) key and value pairs.<br/><br/>**Add:** Required<br/>**Update:** Optional|[CustomParameter](../campaign-api/customparameter-data-object.md) array|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Campaign](../campaign-api/campaign-data-object.md)  
[AdGroup](../campaign-api/adgroup-data-object.md)  
[Keyword](../campaign-api/keyword-data-object.md)  
[Ad](../campaign-api/ad-data-object.md)  
[SiteLink](../campaign-api/sitelink-data-object.md)  
[AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md)  

