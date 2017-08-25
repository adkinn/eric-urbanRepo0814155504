---
title: "ShoppingSetting Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c53e787-9d62-45db-af59-7ef7dd13a0c4
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ShoppingSetting Data Object
Defines the campaign level settings for a Bing Shopping Campaign.

## Syntax

```xml
<xs:complexType name="ShoppingSetting">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Setting">
      <xs:sequence>
        <xs:element minOccurs="0" name="LocalInventoryAdsEnabled" nillable="true" type="xs:boolean"/>
        <xs:element minOccurs="0" name="Priority" nillable="true" type="xs:int"/>
        <xs:element minOccurs="0" name="SalesCountryCode" nillable="true" type="xs:string"/>
        <xs:element minOccurs="0" name="StoreId" nillable="true" type="xs:long"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ShoppingSetting* object derives from the [Setting](../campaign-api/setting-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.


|Element|Description|Data Type|
|-----------|---------------|-------------|
|*LocalInventoryAdsEnabled*|Determines whether local inventory ads are enabled for the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store.<br/><br/>**Note:** [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]<br/><br/>Set this property to *true* if you want to enable local inventory ads, and otherwise set it to *false*.<br/><br/>**Add:** Optional. If you do not specify this field or leave it empty, the default value of *false* will be set and local inventory ads will not be enabled.<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*boolean*|
|*Priority*|Helps determine which [!INCLUDE[brand_bsc](../campaign-api/includes/brand-bsc.md)] campaign  serves ads, in the event that two or more campaigns use the product catalog feed from the same [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store.<br /><br />You must specify one of the supported values: 0, 1, or 2. The higher numbers are given higher priority.<br /><br />If two shopping campaigns use the product catalog feed from same [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store, then  ads will be delivered for the [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) with the highest bid.<br /><br />**Note:** In the [!INCLUDE[brand](../campaign-api/includes/brand.md)] web application, the default priority selected is "Low" which is the equivalent of '0'.<br/><br/>**Add:** Required<br/>**Update:** Optional|*int*|
|*SalesCountryCode*|The country code for the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store. To get the list of supported country codes use the [GetBSCCountries](../campaign-api/getbsccountries-service-operation.md) operation.<br/><br/>**Add:** Required<br/>**Update:** Read-only|*string*|
|*StoreId*|The unique identifier for the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store that your product catalog feed belongs to.<br /><br />To get the *StoreId*, call the [GetBMCStoresByCustomerId](../campaign-api/getbmcstoresbycustomerid-service-operation.md) operation. The *Id* element of a [BMCStore](../campaign-api/bmcstore-data-object.md) corresponds to this *StoreId*.<br/><br/>**Add:** Required<br/>**Update:** Read-only|*long*|

## <a name="InheritedElements"></a>Inherited Elements
The *ShoppingSetting* object derives from the [Setting](../campaign-api/setting-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to shopping settings, and might not apply to other objects that inherit the same elements from the [Setting](../campaign-api/setting-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the setting. This value is *Shopping* when you retrieve a shopping setting. For more information about setting types, see the [Setting Data Object Remarks](../campaign-api/setting-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddCampaigns](../campaign-api/addcampaigns-service-operation.md)  
[GetCampaignsByAccountId](../campaign-api/getcampaignsbyaccountid-service-operation.md)  
[GetCampaignsByIds](../campaign-api/getcampaignsbyids-service-operation.md)  
[UpdateCampaigns](../campaign-api/updatecampaigns-service-operation.md)  
[Campaign](../campaign-api/campaign-data-object.md)  
[Setting](../campaign-api/setting-data-object.md)  

