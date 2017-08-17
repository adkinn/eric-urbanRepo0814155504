---
title: "DataType Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7546f4a0-7ee7-4c23-9718-a8b27c610f5e
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DataType Value Set
Defines the possible formats in which to generate the billing document.

## Syntax

```xml
\<xs:simpleType name="DataType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Xml"/>
    \<xs:enumeration value="Pdf"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Pdf|Use PDF format.|
|Xml|Use XML format.|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]