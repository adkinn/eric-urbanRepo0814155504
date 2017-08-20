---
title: "CustomAudience Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80f29fd7-5d80-4cbe-aa8e-9b45562b2773
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
---
# CustomAudience Data Object
Defines a custom audience. 

> [!NOTE]
> Only update of the *Description* is supported. You cannot add or delete a custom audience using the Bing Ads API.


> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]

## Syntax

```xml
\<xs:complexType name="CustomAudience">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:Audience">
      \<xs:sequence />
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *CustomAudience* object inherits elements from the [Audience](../campaign-api/audience-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

## <a name="InheritedElements"></a>Inherited Elements
The *CustomAudience* object inherits the following elements from the [Audience](../campaign-api/audience-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to custom audiences, and might not apply to other objects that inherit the same elements from the [Audience](../campaign-api/audience-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Description*|The description of the audience. Use a description to help you remember what audience you are targeting.<br/><br/>The description can contain a maximum of 1,024 characters.<br/><br/>**Add:** Not supported<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *Audience* object.|*KeyValuePairOfstringstring* array|
|*Id*|The Bing Ads identifier of the audience.<br/><br/>**Add:** Not supported<br/>**Update:** Required and read-only|*long*|
|*MembershipDuration*|The membership duration determines how far back in time Bing Ads should look for actions that match your custom audience definition in order to add people to your list. For a custom audience the membership duration is not set in the Bing Ads web application, and Bing Ads defers to your custom audience provider settings.<br/><br/>When you request the custom audience via Bing Ads API, the returned membership duration will be null.<br/><br/>**Add:** Not supported<br/>**Update:** Not supported|*int*|
|*Name*|The name of the audience. The name can contain a maximum of 128 characters.<br/><br/>**Add:** Not supported<br/>**Update:** Read-only|*string*|
|*ParentId*|The Bing Ads identifier of the account or customer. <br/><br/>If the *Scope* is set to *Account*, this is the account ID, and otherwise it is the customer ID.<br/><br/>**Add:** Not supported<br/>**Update:** Read-only. You cannot change the parent ID.|*long*|
|*Scope*|Scope defines what accounts can use this audience.<br/><br/> If scope is set to *Account*, the audience can only be associated with ad groups within one specified account (*ParentId*). If scope is set to *Customer*, the audience can be associated with any ad groups across all of the customer's accounts.<br/><br/>**Add:** Not supported<br/>**Update:** Read-only. You cannot change the scope.|[EntityScope](../campaign-api/entityscope-value-set.md)|
|*Type*|The type of the audience. This value is *Custom* when you retrieve a custom audience. For more information about audience types, see the [Audience Data Object Remarks](../campaign-api/audience-data-object.md#remarks).<br /><br />**Add:** Not supported<br/>**Update:** Read-only|[AudienceType](../campaign-api/audiencetype-value-set.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[Audience](../campaign-api/audience-data-object.md)  
