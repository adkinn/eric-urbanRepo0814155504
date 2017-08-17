---
title: "RuleItemGroup Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 341896f3-8b69-4d43-85e4-ea19a3e26b7f
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# RuleItemGroup Data Object
Defines an object that contains a list of remarketing list rule items that apply to the same visited page. 

## Syntax

```xml
\<xs:complexType name="RuleItemGroup">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Items" nillable="true" type="tns:ArrayOfRuleItem"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Items*|The list of rule items.<br/><br/>The maximum number of rule items in a rule item group is 100. The rule items must all be of the same concrete type derived from the [RuleItem](../campaign-api/ruleitem-data-object.md) base class. Currently only a list of [StringRuleItem](../campaign-api/stringruleitem-data-object.md) objects are supported.<br/><br/>The list of [StringRuleItem](../campaign-api/stringruleitem-data-object.md) objects apply to same visited page, and the rule conditions are joined using the logical *AND* operator. In other words to add a visitor to the remarketing list, one page must meet all of the conditions in this rule item list. To create a list of rules for another page, you must add a separate *RuleItemGroup*.<br/><br/>**Add:** Required<br/>**Update:** Optional. If you want to keep any of the previous rule items, then you must explicitly set them again during update.|[RuleItem](../campaign-api/ruleitem-data-object.md) array|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  