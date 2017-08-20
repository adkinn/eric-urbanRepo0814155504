---
title: "CampaignStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfb2fdf6-7f95-49e0-811d-ed5302bb5392
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignStatus Value Set
Defines the possible status values of a campaign.

## Syntax

```xml
<xs:simpleType name="CampaignStatus">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Active" />
    <xs:enumeration value="Paused" />
    <xs:enumeration value="BudgetPaused" />
    <xs:enumeration value="BudgetAndManualPaused" />
    <xs:enumeration value="Deleted" />
    <xs:enumeration value="Suspended" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The campaign is active, which indicates that the campaign’s ads can be served.|
|BudgetAndManualPaused|The campaign is paused, which indicates that the campaign’s ads will not serve. This status results when a user sets the campaign status to paused after the service pauses the campaign because the budget is depleted.|
|BudgetPaused|The campaign is paused, which indicates that the campaign’s ads will not serve. The service sets this status when the budget is depleted. The service will set the status back to *Active* when the budget is restored.|
|Deleted|The campaign is deleted. This status is for internal use only. Because all Get operations do not return deleted objects, you will not see an object with this status.|
|Paused|The campaign is paused, which indicates that the campaign’s ads will not serve.|
|Suspended|Your campaign has been suspended and no ads are eligible for delivery because of potentially fraudulent activity. <br />Please contact [Bing Ads Support](http://go.microsoft.com/fwlink/?LinkId=269631).|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Campaign](../campaign-api/campaign-data-object.md)

