---
title: "AudienceType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dbb7612-03a5-4055-b7fe-59f141cc62c4
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
---
# AudienceType Value Set
Defines the possible audience types.

## Syntax

```xml
<xs:simpleType name="AudienceType">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="RemarketingList" />
        <xs:enumeration value="Custom" />
        <xs:enumeration value="InMarket" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Custom|The audience is a custom audience.|
|InMarket|The audience is an in-market audience.|
|RemarketingList|The audience is a remarketing list.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Audience](../campaign-api/audience-data-object.md)  

