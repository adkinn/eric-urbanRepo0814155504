---
title: "KeywordStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 096a79db-bd28-4b78-9010-252f4e337b52
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordStatus Value Set
Defines the possible status values of a keyword.

## Syntax

```xml
\<xs:simpleType name="KeywordStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Active" />
    \<xs:enumeration value="Paused" />
    \<xs:enumeration value="Deleted" />
    \<xs:enumeration value="Inactive" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The keyword can be used to match user search queries.|
|Deleted|This status is for internal use only. Because all Get operations do not return deleted objects, you will not see an object with this status.|
|Inactive|The keyword is undergoing editorial review or has failed editorial review. To determine the keyword editorial status, see [KeywordEditorialStatus](../campaign-api/keywordeditorialstatus-value-set.md).|
|Paused|The keyword cannot be used to match user search queries until the owner resumes it.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Keyword](../campaign-api/keyword-data-object.md)

