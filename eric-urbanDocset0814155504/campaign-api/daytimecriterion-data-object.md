---
title: "DayTimeCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bde294e1-44c1-49bc-8949-bbad04b0aaa2
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
---
# DayTimeCriterion Data Object
Defines a criterion that can be used to show ads to users during a specific day and time range.

The *DayTimeCriterion* criterion can be included within [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) and [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) objects. If ad group level day and time criterions are specified, the campaign level day and time criterions are ignored for that ad group. In other words the ad group day and time criterions override the campaign day and time criterions, and are not applied as a union.   

[!INCLUDE[guide_target_to_criterions](../campaign-api/includes/guide-target-to-criterions.md)]

## Syntax

```xml
<xs:complexType name="DayTimeCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element name="Day" type="tns:Day" minOccurs="0" nillable="true"/>
        <xs:element name="FromHour" type="xs:int" minOccurs="0" nillable="true"/>
        <xs:element name="FromMinute" type="tns:Minute" minOccurs="0" nillable="true"/>
        <xs:element name="ToHour" type="xs:int" minOccurs="0" nillable="true"/>
        <xs:element name="ToMinute" type="tns:Minute" minOccurs="0" nillable="true"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *DayTimeCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Day*|The day of the week to target. For example, you can target the ads to run only on Friday or Saturday.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting. |[Day](../campaign-api/day-value-set.md)|
|*FromHour*|The starting hour range to target.<br/><br/>The possible values range from 0 to 23.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting. |*int*|
|*FromMinute*|The starting minute of the hour to target.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting. |[Minute](../campaign-api/minute-value-set.md)|
|*ToHour*|The ending hour range to target.<br/><br/>The possible values range from 0 to 23.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting. |*int*|
|*ToMinute*|The ending minute of the hour to target.<br/><br/>**Add:** Required<br/>**Update:** Not allowed. If you specify this element it must match the existing setting. |[Minute](../campaign-api/minute-value-set.md)|


## <a name="InheritedElements"></a>Inherited Elements
The *DayTimeCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following element. 

> [!NOTE]
> The descriptions below are specific to day and time criterions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *DayTime* when you retrieve a day and time criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
