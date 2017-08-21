---
title: "DynamicSearchAdsSetting Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe5176bb-7265-4723-a04d-62b778af5ca5
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DynamicSearchAdsSetting Data Object
Defines the campaign level settings for a Dynamic Search Ads campaign.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]

## Syntax

```xml
<xs:complexType name="DynamicSearchAdsSetting">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Setting">
      <xs:sequence>
        <xs:element minOccurs="0" name="DomainName" nillable="true" type="xs:string"/>
        <xs:element minOccurs="0" name="Language" nillable="true" type="xs:string"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *DynamicSearchAdsSetting* object derives from the [Setting](../campaign-api/setting-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.


|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DomainName*|The domain name of the website that you want to target for dynamic search ads.<br/><br/>The length of the string is limited to 2,048 characters. If the domain name includes *www* it will be trimmed and not used.<br/><br/>**Add:** Required<br/>**Update:** Read-only. You cannot update the domain name.|*string*|
|*Language*|The language of the website pages that you want to target for dynamic search ads. Currently the only supported language code is 'en'.<br/><br/>**Add:** Required<br/>**Update:** Read-only. You cannot update the language.|*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *DynamicSearchAdsSetting* object derives from the [Setting](../campaign-api/setting-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to dynamic search ads settings, and might not apply to other objects that inherit the same elements from the [Setting](../campaign-api/setting-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the setting. This value is *DynamicSearchAds* when you retrieve a dynamic search ads setting. For more information about setting types, see the [Setting Data Object Remarks](../campaign-api/setting-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddCampaigns](../campaign-api/addcampaigns-service-operation.md)  
[GetCampaignsByAccountId](../campaign-api/getcampaignsbyaccountid-service-operation.md)  
[GetCampaignsByIds](../campaign-api/getcampaignsbyids-service-operation.md)  
[UpdateCampaigns](../campaign-api/updatecampaigns-service-operation.md)  
[Campaign](../campaign-api/campaign-data-object.md)  
[Setting](../campaign-api/setting-data-object.md)  

