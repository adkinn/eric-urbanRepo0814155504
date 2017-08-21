---
title: "EmailFormat Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b51c1ac-3f5e-460d-9c00-c15f9e265a07
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EmailFormat Value Set
Defines the possible formats of the body of an email message.

## Syntax

```xml
<xs:simpleType name="EmailFormat">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Html" />
    <xs:enumeration value="Text" />
  </xs:restriction>
</xs:simpleType>
```

## Members

|Member|Description|
|----------|---------------|
|Html|The format of the body of the email message is HTML.|
|Text|The format of the body of the email message is plain text.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
