---
title: "EntityNegativeKeyword Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7221368b-4e46-43bd-8144-de0b415514a7
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EntityNegativeKeyword Data Object
Defines an object that contains a set of negative keywords that are only associated with the corresponding entity such as a campaign or ad group.

## Syntax

```xml
\<xs:complexType name="EntityNegativeKeyword">
  \<xs:sequence>
    \<xs:element name="EntityId" type="xs:long" />
    \<xs:element name="EntityType" nillable="true" type="xs:string" />
    \<xs:element name="NegativeKeywords" nillable="true" type="tns:ArrayOfNegativeKeyword" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityId*|The system-generated identifier of a campaign or ad group that is associated with the negative keywords.|*long*|
|*EntityType*|The type of entity such as a campaign that is associated with the negative keywords.<br /><br />The possible values are *AdGroup* and *Campaign*.|*string*|
|*NegativeKeywords*|An array of negative keywords that are associated with the corresponding campaign or ad group.|[NegativeKeyword](../campaign-api/negativekeyword-data-object.md) array|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddNegativeKeywordsToEntities](../campaign-api/addnegativekeywordstoentities-service-operation.md)  
[DeleteNegativeKeywordsFromEntities](../campaign-api/deletenegativekeywordsfromentities-service-operation.md)  
[GetNegativeKeywordsByEntityIds](../campaign-api/getnegativekeywordsbyentityids-service-operation.md)  

