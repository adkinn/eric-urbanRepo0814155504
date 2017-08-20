---
title: "Paging Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d25ac23b-b677-474a-97c2-e2c1bbab2a68
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
---
# Paging Data Object
Defines a paging object that you can use to request labels and label associations in batches.

## Syntax

```xml
<xs:complexType name="Paging">
  <xs:sequence>
    <xs:element name="Index" type="xs:int" minOccurs="0"/>
    <xs:element name="Size" type="xs:int" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Index*|The zero-based results page index. For example to request the first page of results, set this value to 0 (zero).|*int*|
|*Size*|The page size and the number of results to return in the specified page. The maximum size is 1,000.|*int*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Label](../campaign-api/label-data-object.md)  
[LabelAssociation](../campaign-api/labelassociation-data-object.md)  
