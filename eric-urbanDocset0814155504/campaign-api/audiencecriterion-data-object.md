---
title: "AudienceCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23cb0741-5e28-4e4d-967d-2841f36afdfe
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
---
# AudienceCriterion Data Object
Defines a criterion that can be used to show ads to a specific audience.

The *AudienceCriterion* criterion can be included within [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) and [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md) objects. 

## Syntax

```xml
<xs:complexType name="AudienceCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element minOccurs="0" name="AudienceId" nillable="true" type="xs:long"/>
        <xs:element minOccurs="0" name="AudienceType" nillable="true" type="tns:AudienceType"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *AudienceCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AudienceId*|The Bing Ads identifier of the [Audience](../campaign-api/audience-data-object.md).<br/><br/>**Add:** Required<br/>**Update:** Read-only. You must leave this element null or the audience must already be associated with the specified entity. To associate a different audience with the entity, you must add a new audience criterion and optionally delete any existing audience criterions.|*long*|
|*AudienceType*|The audience type.<br/><br/>**Add:** Required<br/>**Update:** Read-only. |[AudienceType](../campaign-api/audiencetype-value-set.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *AudienceCriterion* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following element. 

> [!NOTE]
> The descriptions below are specific to audience criterions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *Audience* when you retrieve an audience criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Criterion](../campaign-api/criterion-data-object.md)  
