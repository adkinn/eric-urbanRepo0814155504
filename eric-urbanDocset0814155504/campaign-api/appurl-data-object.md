---
title: "AppUrl Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dab591c-0275-44be-9baa-70e6e1d64e12
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AppUrl Data Object
Defines the operating system platform and URL of the app store download webpage.

> [!NOTE]
> Reserved for future use.

## Syntax

```xml
\<xs:complexType name="AppUrl">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="OsType" nillable="true" type="xs:string"/>
    \<xs:element minOccurs="0" name="Url" nillable="true" type="xs:string"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*OsType*|Reserved for future use.|*string*|
|*Url*|Reserved for future use.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]


