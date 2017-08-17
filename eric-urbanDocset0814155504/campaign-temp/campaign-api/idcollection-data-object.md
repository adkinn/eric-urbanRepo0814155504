---
title: "IdCollection Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40b022b5-8a1a-4943-95fd-41aaea689c32
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# IdCollection Data Object
Defines an object that contains a list of entity identifiers.

## Syntax

```xml
\<xs:complexType name="IdCollection">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Ids" nillable="true" type="q53:ArrayOfNullableOflong" xmlns:q53="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Ids*|A list of entity identifiers.|*long* array|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddNegativeKeywordsToEntities](../campaign-api/addnegativekeywordstoentities-service-operation.md)  
[GetCampaignIdsByBudgetIds](../campaign-api/getcampaignidsbybudgetids-service-operation.md)  

