---
title: "ConversionGoalTrackingStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c4fe9b9-8109-4a73-8a89-57103d95d9c6
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ConversionGoalTrackingStatus Value Set
Defines the possible system-determined status values of a conversion goal. These are the status values that can be set by the system, for example the system sets the status to *TagUnverified* if the UET tag has not yet been verified. 

> [!NOTE]
> For most goals (all except [AppInstallGoal](../campaign-api/appinstallgoal-data-object.md)), the *ConversionGoalTrackingStatus* depends in part on the system-determined [UetTagTrackingStatus](../campaign-api/uettagtrackingstatus-value-set.md) of the [UetTag](../campaign-api/uettag-data-object.md) that is associated with the [ConversionGoal](../campaign-api/conversiongoal-data-object.md). If the [UetTagTrackingStatus](../campaign-api/uettagtrackingstatus-value-set.md) is *Active* then the conversion goal tracking status can be either *NoRecentConversions* or *RecordingConversions*, and otherwise the conversion goal tracking status mirrors the tag status. For details please see the descriptions below. 

For status values that a user can decide to set, for example setting the status to *Paused* if you no longer wish to track conversions for that goal, see [ConversionGoalStatus](../campaign-api/conversiongoalstatus-value-set.md).   

## Syntax

```xml
\<xs:simpleType name="ConversionGoalTrackingStatus">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="TagUnverified" />
        \<xs:enumeration value="NoRecentConversions" />
        \<xs:enumeration value="RecordingConversions" />
        \<xs:enumeration value="TagInactive" />
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|NoRecentConversions|The [UetTagTrackingStatus](../campaign-api/uettagtrackingstatus-value-set.md) is *Active*, but we haven't recorded any conversions in the last 7 days. This is most likely because you either have created the goal incorrectly, have not tagged your entire website i.e. the pages that have the conversion action, or you don't have any users converting on your site. |
|RecordingConversions|The [UetTagTrackingStatus](../campaign-api/uettagtrackingstatus-value-set.md) is *Active*, and we have recorded conversions within the last 7 days.|
|TagInactive|The [UetTagTrackingStatus](../campaign-api/uettagtrackingstatus-value-set.md) is *Inactive*, and Bing Ads has not received any user activity data from the UET tag in the last 24 hours. Make sure that the UET tag tracking code is still on your website. |
|TagUnverified|The [UetTagTrackingStatus](../campaign-api/uettagtrackingstatus-value-set.md) is *Unverified*, and Bing Ads hasn’t received any user activity data from the UET tag on your website. It can take up to 24 hours for Bing Ads to verify. If you still see this status, you either have not added the UET tag tracking code to your website or there is an issue with the setup that you need to fix. |

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[ConversionGoalStatus](../campaign-api/conversiongoalstatus-value-set.md)  
[UetTag](../campaign-api/uettag-data-object.md)  
[UetTagTrackingStatus](../campaign-api/uettagtrackingstatus-value-set.md)  
