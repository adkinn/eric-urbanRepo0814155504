---
title: "RemarketingList Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac49ac45-211e-4a0f-b2be-7b8f53387351
caps.latest.revision: 17
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# RemarketingList Data Object
Defines a remarketing list.

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]

## Syntax

```xml
\<xs:complexType name="RemarketingList">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:Audience">
      \<xs:sequence>
        \<xs:element name="Rule" type="tns:RemarketingRule" minOccurs="0"/>
        \<xs:element name="TagId" type="xs:long" minOccurs="0"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *RemarketingList* object inherits elements from the [Audience](../campaign-api/audience-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Rule*|A rule includes conditions used to determine who to add to your remarketing list.<br /><br />You can choose one of the four types of rules to target different audiences: [CustomEventsRule](../campaign-api/customeventsrule-data-object.md), [PageVisitorsRule](../campaign-api/pagevisitorsrule-data-object.md), [PageVisitorsWhoDidNotVisitAnotherPageRule](../campaign-api/pagevisitorswhodidnotvisitanotherpagerule-data-object.md), and [PageVisitorsWhoVisitedAnotherPageRule](../campaign-api/pagevisitorswhovisitedanotherpagerule-data-object.md).<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]If you want to keep any of the previous rule items, then you must explicitly set them again during update. You can choose to change the type of rule during update.|[RemarketingRule](../campaign-api/remarketingrule-data-object.md)|
|*TagId*|The Bing Ads identifier of the Universal Event Tracking (UET) tag that is used with the remarketing list.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*long*|

## <a name="InheritedElements"></a>Inherited Elements
The *RemarketingList* object inherits the following elements from the [Audience](../campaign-api/audience-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to remarketing lists, and might not apply to other objects that inherit the same elements from the [Audience](../campaign-api/audience-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Description*|The description of the audience. Use a description to help you remember what audience you are targeting.<br/><br/>The description can contain a maximum of 1,024 characters.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *Audience* object.|*KeyValuePairOfstringstring* array|
|*Id*|The Bing Ads identifier of the audience.<br/><br/>**Add:** Read-only<br/>**Update:** Required and read-only|*long*|
|*MembershipDuration*|When you create an audience, you can specify how far back in time Bing Ads should look for actions that match your audience definition.<br/><br/>The mimimum duration is 1 day and the maximum duration allowed is 180 days.<br/><br/>**Add:** Optional. If not specified, the membership duration will be set to 30 by default.<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*int*|
|*Name*|The name of the audience. The name can contain a maximum of 128 characters.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*ParentId*|The Bing Ads identifier of the account or customer. <br/><br/>If the *Scope* is set to *Account*, this is the account ID, and otherwise it is the customer ID.<br/><br/>**Add:** Required<br/>**Update:** Read-only. You cannot change the parent ID.|*long*|
|*Scope*|Scope defines what accounts can use this audience.<br/><br/> If scope is set to *Account*, the audience can only be associated with ad groups within one specified account (*ParentId*). If scope is set to *Customer*, the audience can be associated with any ad groups across all of the customer's accounts.<br/><br/>**Add:** Required<br/>**Update:** Read-only. You cannot change the scope.|[EntityScope](../campaign-api/entityscope-value-set.md)|
|*Type*|The type of the audience. This value is *RemarketingList* when you retrieve a remarketing list audience. For more information about audience types, see the [Audience Data Object Remarks](../campaign-api/audience-data-object.md#remarks).<br /><br />**Add:** Read-only<br/>**Update:** Read-only|[AudienceType](../campaign-api/audiencetype-value-set.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[Audience](../campaign-api/audience-data-object.md)  
