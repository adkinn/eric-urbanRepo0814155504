---
title: "AccountType Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60c3ea57-0c24-4870-afee-12b63d26f310
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountType Value Set
Defines the possible account types.

## Syntax

```xml
\<xs:simpleType name="AccountType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Advertiser" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Advertiser|An advertiser account.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]