---
title: "Keyword Best Position Bid"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 736ed66a-bec5-4574-ab0e-46f378bc10bc
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Keyword Best Position Bid
Defines a keyword's estimated best position bid that can be downloaded in a bulk file.

## <a name="keywordbestpositionbid"></a>Keyword Best Position Bid Record
For a *Keyword Best Position Bid* record, the following bulk fields are available for download. The keyword best position bid is equivalent to calling the [GetEstimatedBidByKeywordIds](https://msdn.microsoft.com/library/bing-ads-ad-insight-getestimatedbidbykeywordids.aspx) operation with the Ad Insight service, and specifying *MainLine1* as the [TargetAdPosition](http://msdn.microsoft.com/library/bing-ads-ad-insight-targetadposition.aspx) value.

|Column Header|Description|
|-----------------|---------------|
|*Keyword*|The keyword to which the estimates apply.|
|*Bid*|The suggested bid value for the best position in search results.|
|*Spend*|The estimated average cost per week.|
|*Impressions*|The estimated average number of impressions per week.|
|*Clicks*|The estimated average number of clicks per week.|
|*CTR*|The estimated CTR.<br /><br />The formula used to calculate the CTR is (maximum number of clicks / maximum number of impressions) &#42; 100.|
|*Avg CPC*|The estimated average CPC.<br /><br />The formula used to calculate the average CPC is (maximum total cost / maximum number of clicks).|
|*Avg CPM*|The average of the cost per thousand impressions (CPM) of the ad.<br/><br/>The value will be 0 (zero) if the ad group to which the ad belongs does not specify the Content ad distribution medium or if the user does not belong to the CPM pilot program.|
|*Avg position*|The position in the search results given the specified bid.|
|*Conversions*|The estimated number of conversions per week.|
|*CPA*|The estimated cost per conversion.<br /><br />The formula for calculating the cost per conversion is (spend / conversions).|
