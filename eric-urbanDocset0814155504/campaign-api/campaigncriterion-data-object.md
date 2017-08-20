---
title: "CampaignCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 742c1da1-b3f2-4f9a-aa0d-ba2da0a3d195
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignCriterion Data Object
Defines a criterion that you want applied to the specified campaign.

Do not try to instantiate a *CampaignCriterion*. You can create one or more following objects that derive from it.
-   [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md)
-   [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md)


## Syntax

```xml
\<xs:complexType name="CampaignCriterion">
  \<xs:sequence>
    \<xs:element name="CampaignId" type="xs:long"/>
    \<xs:element minOccurs="0" name="Criterion" nillable="true" type="tns:Criterion"/>
    \<xs:element xmlns:q76="http://schemas.datacontract.org/2004/07/System.Collections.Generic" minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q76:ArrayOfKeyValuePairOfstringstring"/>
    \<xs:element minOccurs="0" name="Id" nillable="true" type="xs:long"/>
    \<xs:element minOccurs="0" name="Status" nillable="true" type="tns:CampaignCriterionStatus"/>
    \<xs:element minOccurs="0" name="Type" nillable="true" type="xs:string"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignId*|The identifier of the campaign to apply the criterion to.|*long*|
|*Criterion*|The criterion to apply to the campaign. The criterion helps determine whether ads in the campaign are served.<br/><br/>For a list of available criterion types, see [CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md).|[Criterion](../campaign-api/criterion-data-object.md)|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for this object.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier for the campaign criterion.|*long*|
|*Status*|A status value that determines whether to apply the criterion to the campaign.|[CampaignCriterionStatus](../campaign-api/campaigncriterionstatus-value-set.md)|
|*Type*|The type of campaign criterion. For more information, see [Remarks](#remarks).|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by whether you instantiate a [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md) or [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md).

If you generate the SOAP manually, use the *type* attribute of the `<CampaignCriterion>` node as shown in the following example, to specify the type of criterion.

```xml
\<CampaignCriterion i:type="BiddableCampaignCriterion" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
    \<Id i:nil="true" />
    \<Status i:nil=”true” />
     . . .
</CampaignCriterion>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddCampaignCriterions](../campaign-api/addcampaigncriterions-service-operation.md)  
[DeleteCampaignCriterions](../campaign-api/deletecampaigncriterions-service-operation.md)  
[GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md)  
[UpdateCampaignCriterions](../campaign-api/updatecampaigncriterions-service-operation.md)  

