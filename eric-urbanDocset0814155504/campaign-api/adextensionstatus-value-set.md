---
title: "AdExtensionStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a26b557-bf5e-421f-9079-ec9ef23eb023
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionStatus Value Set
Defines the possible status values of an ad extension.

## Syntax

```xml
<xs:simpleType name="AdExtensionStatus">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Active" />
    <xs:enumeration value="Deleted" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The ad extension is active. You can associate an active ad extension with a campaign or ad group.|
|Deleted|The ad extension is deleted. This status is for internal use only. The Get operations will not include deleted extensions.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtension](../campaign-api/adextension-data-object.md)

