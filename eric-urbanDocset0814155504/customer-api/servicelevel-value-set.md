---
title: "ServiceLevel Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 939c4655-c86d-4339-8841-b540a605eefa
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ServiceLevel Value Set
For internal use only.

## Syntax

```xml
\<xs:simpleType name="ServiceLevel">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="SelfServe" />
    \<xs:enumeration value="SelfServeTrusted" />
    \<xs:enumeration value="Premium" />
    \<xs:enumeration value="Internal" />
    \<xs:enumeration value="Select" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Internal|For internal use only.|
|Premium|For internal use only.|
|Select|For internal use only.|
|SelfServe|For internal use only.|
|SelfServeTrusted|For internal use only.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]