---
title: "UetTagTrackingStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92761cde-7642-472c-86e7-c03488db8d0e
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UetTagTrackingStatus Value Set
Defines the possible system-determined status values of a UET tag. These are the status values that can be set by the system, for example the system sets the status to *Unverified* if the UET tag has not yet been verified. 

> [!NOTE]
> The *UetTagTrackingStatus* in part influences the system-determined [ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md) of any [ConversionGoal](../campaign-api/conversiongoal-data-object.md) that is associated with the [UetTag](../campaign-api/uettag-data-object.md). If the *UetTagTrackingStatus* is *Active* then the [ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md) can be either *NoRecentConversions* or *RecordingConversions*, and otherwise the conversion goal tracking status mirrors the tag status.  

## Syntax

```xml
<xs:simpleType name="UetTagTrackingStatus">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Unverified" />
        <xs:enumeration value="Active" />
        <xs:enumeration value="Inactive" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active| Your UET tag is working and sending user activity data to Bing Ads.|
|Inactive|Bing Ads has not received any user activity data from the UET tag in the last 24 hours. Make sure that the UET tag tracking code is still on your website.|
|Unverified|Bing Ads hasn’t received any user activity data from the UET tag on your website. It can take up to 24 hours for Bing Ads to verify. If you still see this status, you either have not added the UET tag tracking code to your website or there is an issue with the setup that you need to fix.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md)  
[UetTag](../campaign-api/uettag-data-object.md)  
