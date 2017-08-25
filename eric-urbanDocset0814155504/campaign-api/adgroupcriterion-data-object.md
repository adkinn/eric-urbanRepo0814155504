---
title: "AdGroupCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eac689da-b4d0-4841-bc05-d00a2512e854
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupCriterion Data Object
Defines a criterion that you want applied to the specified ad group.

Do not try to instantiate an *AdGroupCriterion*. You can create one or more following objects that derive from it.
-   [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)
-   [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md)

## Syntax

```xml
<xs:complexType name="AdGroupCriterion">
  <xs:sequence>
    <xs:element minOccurs="0" name="AdGroupId" type="xs:long" />
    <xs:element minOccurs="0" name="Criterion" nillable="true" type="tns:Criterion" />
    <xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
    <xs:element minOccurs="0" name="Status" type="tns:AdGroupCriterionStatus" />
    <xs:element minOccurs="0" name="Type" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|The identifier of the ad group to apply the criterion to.|*long*|
|*Criterion*|The criterion to apply to the ad group. The criterion helps determine whether ads in the ad group are served.<br/><br/>For a list of available criterion types, see [AdGroupCriterionType](../campaign-api/adgroupcriteriontype-value-set.md).|[Criterion](../campaign-api/criterion-data-object.md)|
|*Id*|The unique Bing Ads identifier for the ad group criterion.|*long*|
|*Status*|A status value that determines whether to apply the criterion to the ad group.|[AdGroupCriterionStatus](../campaign-api/adgroupcriterionstatus-value-set.md)|
|*Type*|The type of ad group criterion. For more information, see [Remarks](#remarks).|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by whether you instantiate a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md).

If you generate the SOAP manually, use the *type* attribute of the `<AdGroupCriterion>` node as shown in the following example, to specify the type of criterion.

```xml
<AdGroupCriterion i:type="BiddableAdGroupCriterion" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
    <Id i:nil="true" />
    <Status i:nil=?true? />
     . . .
</AdGroupCriterion>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddAdGroupCriterions](../campaign-api/addadgroupcriterions-service-operation.md)  
[DeleteAdGroupCriterions](../campaign-api/deleteadgroupcriterions-service-operation.md)  
[GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md)  
[UpdateAdGroupCriterions](../campaign-api/updateadgroupcriterions-service-operation.md)  

