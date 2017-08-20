---
title: "CompetitionLevel Value Set"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4f9c3ad-57d5-4624-80cb-e21cb2367a68
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CompetitionLevel Value Set
Competition levels are defined by the number of advertisers bidding on this keyword, relative to all other keywords across Bing Ads. 

You can specify competition levels when calling the [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md) operation.

## Syntax

```xml
<xs:simpleType name="CompetitionLevel">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Low">
    <xs:enumeration value="Medium">
    <xs:enumeration value="High">
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|High|The competition level is high.|
|Low|The competition level is low.|
|Medium|The competition level is medium.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  

