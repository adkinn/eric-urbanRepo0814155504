---
title: "UetTag Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 072e62a2-3dc5-4d9f-86af-387a4fc8cdfd
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UetTag Data Object
Defines a Universal Event Tracking (UET) tag that you can add to your website to allow Bing Ads to collect actions people take on your website.

After you create a UET tag (e.g. via [AddUetTags](../campaign-api/adduettags-service-operation.md)), the next step is to add the UET tag tracking code to your website. We recommend that you, or your website administrator, add it to your entire website in either the head or body sections. If your website has a master page, then that is the best place to add it because you add it once and it is included on all pages. For more information, see [How do I add the UET tag to my website?](https://help.bingads.microsoft.com/#apex/3/en/56688/2).

You can use one UET tag with all of your conversion goals and remarketing lists. Before you create multiple UET tags, see [Reasons for creating more than one UET tag](https://help.bingads.microsoft.com/#apex/3/en/56685/2).

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]

## Syntax

```xml
<xs:complexType name="UetTag">
  <xs:sequence>
    <xs:element name="Description" type="xs:string" nillable="true" minOccurs="0"/>
    <xs:element name="Id" type="xs:long" nillable="true" minOccurs="0"/>
    <xs:element name="Name" type="xs:string" nillable="true" minOccurs="0"/>
    <xs:element name="TrackingNoScript" type="xs:string" nillable="true" minOccurs="0"/>
    <xs:element name="TrackingScript" type="xs:string" nillable="true" minOccurs="0"/>
    <xs:element name="TrackingStatus" type="tns:UetTagTrackingStatus" nillable="true" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Description*|Text to help you identify the UET tag. We recommend that you set this to the related website page name or URL.<br /><br />**Add:** Optional<br />**Update:** Optional|*string*|
|*Id*|The unique Bing Ads identifier of the UET tag.<br /><br />**Add:** Read-only<br />**Update:** Required and Read-only|*long*|
|*Name*|The UET tag name.<br/><br/>The maximum length of the name is 100, and the name must be unique among all UET tags belonging to the same customer.<br /><br />**Add:** Required<br />**Update:** Optional|*string*|
|*TrackingNoScript*|If your website doesn?t support JavaScript, you can use this Non-JavaScript representation of the UET tag. If you use Non-JavaScript, you can?t track custom events or variable revenue.<br /><br />**Add:** Read-only<br />**Update:** Read-only|*string*|
|*TrackingScript*|The tracking script that you can add to your website to allow Bing Ads to collect actions people take on your website.<br /><br />**Add:** Read-only<br />**Update:** Read-only|*string*|
|*TrackingStatus*|The system-determined status values of a UET tag, for example the system sets the status to *Unverified* if the UET tag has not yet been verified.<br /><br />**Add:** Read-only<br />**Update:** Read-only|[UetTagTrackingStatus](../campaign-api/uettagtrackingstatus-value-set.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[AddUetTags](../campaign-api/adduettags-service-operation.md)  
[GetUetTagsByIds](../campaign-api/getuettagsbyids-service-operation.md)  
[UpdateUetTags](../campaign-api/updateuettags-service-operation.md)  
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  
