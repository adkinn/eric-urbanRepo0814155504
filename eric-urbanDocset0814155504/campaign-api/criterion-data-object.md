---
title: "Criterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6469132-704e-41ef-95bc-63aa9f2ee18b
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Criterion Data Object
Defines the base object of a criterion.

Do not try to instantiate a *Criterion*. You can create one or more following objects that derive from it.
-  [AgeCriterion](../campaign-api/agecriterion-data-object.md)  
-  [AudienceCriterion](../campaign-api/audiencecriterion-data-object.md)  
-  [DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md)  
-  [DeviceCriterion](../campaign-api/devicecriterion-data-object.md)  
-  [GenderCriterion](../campaign-api/gendercriterion-data-object.md)  
-  [LocationCriterion](../campaign-api/locationcriterion-data-object.md)  
-  [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md)  
-  [ProductScope](../campaign-api/productscope-data-object.md)  
-  [ProductPartition](../campaign-api/productpartition-data-object.md)  
-  [RadiusCriterion](../campaign-api/radiuscriterion-data-object.md)  
-  [Webpage](../campaign-api/webpage-data-object.md)  

For a list of criterion types that you can use with [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md), see the [CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md) value set.

For a list of criterion types that you can use with [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md), see the [AdGroupCriterionType](../campaign-api/adgroupcriteriontype-value-set.md) value set.

## Syntax

```xml
<xs:complexType name="Criterion">
  <xs:sequence>
    <xs:element minOccurs="0" name="Type" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of criterion. For more information, see [Remarks](#remarks).|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by whether you instantiate a location or other criterion type.

If you generate the SOAP manually, use the *type* attribute of the `<Criterion>` node to specify the type of criterion, as shown in the following example.

```xml
<Criterion i:type="LocationCriterion" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
   . . .
</Criterion>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md)  
[AdGroupCriterionType](../campaign-api/adgroupcriteriontype-value-set.md)  
[CampaignCriterion](../campaign-api/campaigncriterion-data-object.md)  
[CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md)  

