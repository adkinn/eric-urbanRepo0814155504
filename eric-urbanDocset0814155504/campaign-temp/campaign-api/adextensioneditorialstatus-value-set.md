---
title: "AdExtensionEditorialStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33119a6d-7c3e-4017-a469-f5686534e296
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionEditorialStatus Value Set
Defines the editorial review status values of an ad extension.

## Syntax

```xml
\<xs:simpleType name="AdExtensionEditorialStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Active" />
    \<xs:enumeration value="Disapproved" />
    \<xs:enumeration value="Inactive" />
    \<xs:enumeration value="ActiveLimited" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The ad extension passed editorial review.|
|ActiveLimited|The ad extension passed editorial review in one or more markets, and one or more elements of the ad extension is undergoing editorial review in another market. For example the ad extension passed editorial review for Canada and is still pending review in the United States.|
|Disapproved|The ad extension failed editorial review.|
|Inactive|One or more elements of the ad extension is undergoing editorial review.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)

