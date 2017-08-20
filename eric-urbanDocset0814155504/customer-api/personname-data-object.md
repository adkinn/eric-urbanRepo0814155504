---
title: "PersonName Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c51146fb-dd0e-40bd-b651-264af56c4f0d
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# PersonName Data Object
Defines the name of a user.

## Syntax

```xml
\<xs:complexType name="PersonName">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="FirstName" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="LastName" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="MiddleInitial" nillable="true" type="xsd:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*FirstName*|The first name of the user. The first name is limited to 100 characters.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*LastName*|The last name of the user. The last name is limited to 100 characters.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*MiddleInitial*|The middle initial of the user. The middle initial is limited to one character.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]