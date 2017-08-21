---
title: "KeywordEditorialStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1b1c9e5-3989-4207-bf56-0f5fd7e17068
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordEditorialStatus Value Set
Defines the editorial review status values of a keyword.

## Syntax

```xml
<xs:simpleType name="KeywordEditorialStatus">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Active" />
    <xs:enumeration value="Disapproved" />
    <xs:enumeration value="Inactive" />
    <xs:enumeration value="ActiveLimited" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The keyword passed editorial review.|
|ActiveLimited|The keyword passed editorial review in one or more markets, and one or more elements of the keyword is undergoing editorial review in another market. For example the keyword passed editorial review for Canada and is still pending review in the United States.|
|Disapproved|The keyword failed editorial review.|
|Inactive|One or more elements of the keyword is undergoing editorial review.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Keyword](../campaign-api/keyword-data-object.md)  
[GetKeywordsByEditorialStatus](../campaign-api/getkeywordsbyeditorialstatus-service-operation.md)  

