---
title: "LanguageType Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4480c64-5aa1-4a30-af5d-b783ab1653e5
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# LanguageType Value Set
Defines a selection of language values.

> [!NOTE]
> The value set defines a broad selection of languages; however, not all languages are supported. For a list of supported languages, see [Ad Languages](~/concepts/ad-languages.md).

## Syntax

```xml
<xs:simpleType name="LanguageType">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Danish" />
    <xs:enumeration value="Dutch" />
    <xs:enumeration value="English" />
    <xs:enumeration value="Finnish" />
    <xs:enumeration value="French" />
    <xs:enumeration value="German" />
    <xs:enumeration value="Italian" />
    <xs:enumeration value="Japanese" />
    <xs:enumeration value="Norwegian" />
    <xs:enumeration value="Portuguese" />
    <xs:enumeration value="Swedish" />
    <xs:enumeration value="Spanish" />
    <xs:enumeration value="Arabic" /> 
    <xs:enumeration value="Hebrew" /> 
    <xs:enumeration value="Korean" /> 
    <xs:enumeration value="Russian" /> 
    <xs:enumeration value="TraditionalChinese" /> 
    <xs:enumeration value="SimplifiedChinese" /> 
  </xs:restriction>
</xs:simpleType>
```

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
