---
title: "SecretQuestion Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce46cea5-b5ee-4a62-b7b8-3424934e0f0c
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SecretQuestion Value Set
Defines the possible secret questions that users can choose from to help them recall their password.

## Syntax

```xml
<xs:simpleType name="SecretQuestion">
  <xs:restriction base="xs:string">
    <xs:enumeration value="None" />
    <xs:enumeration value="FavoritePetsName" />
    <xs:enumeration value="FavoriteMovie" />
    <xs:enumeration value="Anniversary" />
    <xs:enumeration value="FatherMiddleName" />
    <xs:enumeration value="SpouseMiddleName" />
    <xs:enumeration value="FirstChildMiddleName" />
    <xs:enumeration value="HighSchoolName" />
    <xs:enumeration value="FavoriteTeacherName" />
    <xs:enumeration value="FavoriteSportsTeam" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Member|Description|
|----------|---------------|
|Anniversary|An anniversary date.|
|FatherMiddleName|The middle name of your father.|
|FavoriteMovie|The title of your favorite movie.|
|FavoritePetsName|The name of your favorite pet.|
|FavoriteSportsTeam|The name of your favorite sports team.|
|FavoriteTeacherName|The name of your favorite teacher.|
|FirstChildMiddleName|The middle name of your first child.|
|HighSchoolName|The name of the high school that you attended.|
|None|Do not specify this value. If you specify this value, adding or updating the user will fail.|
|SpouseMiddleName|The middle name of your spouse.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
