---
title: "RuleItem Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c91e2f0-d220-4925-a635-a1af9c008853
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# RuleItem Data Object
Defines the base class of a remarketing list rule item.

Do not try to instantiate a *RuleItem*. You can create one or more following objects that derive from it.
- [StringRuleItem](../campaign-api/stringruleitem-data-object.md)

## Syntax

```xml
\<xs:complexType name="RuleItem">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Type" nillable="true" type="xs:string"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of rule item. For more information, see [Remarks](#remarks).|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by the type of rule item that you instantiate.

If you generate the SOAP manually, use the *type* attribute of the `<RuleItem>` node as shown in the following example, to specify that the rule item is a string rule item.

```xml
\<e145:Items p4:nil="false">
  \<e145:RuleItem p4:type="StringRuleItem">
    \<e145:Operand p4:nil="false">Url\</e145:Operand>
    \<e145:Operator>Contains\</e145:Operator>
    \<e145:Value p4:nil="false">xyz\</e145:Value>
  \</e145:RuleItem>
\</e145:Items>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  