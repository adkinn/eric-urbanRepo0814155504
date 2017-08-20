---
title: "StringRuleItem Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0304e0b3-24af-453f-8bfe-085d7ca323df
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# StringRuleItem Data Object
Defines a rule expression that depends on the string values of the Url or Referrer Url.

## Syntax

```xml
<xs:complexType name="StringRuleItem">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:RuleItem">
      <xs:sequence>
        <xs:element minOccurs="0" name="Operand" nillable="true" type="xs:string"/>
        <xs:element xmlns:q8="https://bingads.microsoft.com/CampaignManagement/v10" minOccurs="0" name="Operator" type="q8:StringOperator"/>
        <xs:element minOccurs="0" name="Value" nillable="true" type="xs:string"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *StringRuleItem* object derives from the [RuleItem](../campaign-api/ruleitem-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Operand*|The rule operand or key on the left hand side of the operator. <br/><br/>Supported values are *Url* and *ReferrerUrl*.<br/><br/>For example to define a rule where the page Url must contain *page.html*, set the *Operand* to *Url*, *Operator* to *Contains*, and *Value* to *page.html*.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*Operator*|The rule item operator.<br/><br/>**Add:** Required<br/>**Update:** Required|[StringOperator](../campaign-api/stringoperator-value-set.md)|
|*Value*|The rule value on the right hand side of the operator.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *StringRuleItem* object derives from the [RuleItem](../campaign-api/ruleitem-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to string rule items, and might not apply to other objects that inherit the same elements from the [RuleItem](../campaign-api/ruleitem-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of rule item. For more information, see [RuleItem Data Object Remarks](../campaign-api/ruleitem-data-object.md#remarks).|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  
