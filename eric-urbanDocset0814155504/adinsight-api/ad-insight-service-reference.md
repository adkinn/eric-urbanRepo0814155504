---
title: "Ad Insight Service Reference"
ms.custom: ""
ms.date: "08/09/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8263375-08db-4c6d-adb8-feeef5332669
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Insight Service Reference
The Ad Insight [service](~/concepts/bing-ads-web-service-addresses.md) defines the following Application Programming Interface (API) that you can use to determine the historical performance of keywords, get the estimated bid and position for a keyword, and to get suggested keywords from an existing keyword or from the content at a specified URL. The service can also help you discover bid, budget, and keyword opportunities.

|Interface|Description|
|---------|---------|
|[Ad Insight Service Operations](../adinsight-api/ad-insight-service-operations.md)|Service operations include [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md), [GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md), [GetBidLandscapeByKeywordIds](../adinsight-api/getbidlandscapebykeywordids-service-operation.md), and more.|
|[Ad Insight Data Objects](../adinsight-api/ad-insight-data-objects.md)|Depending on whether you want to get the historical performance of keywords, the estimated bid and position for a keyword, or suggested keywords from an existing keywords, data objects include [HistoricalSearchCountPeriodic](../adinsight-api/historicalsearchcountperiodic-data-object.md), [TrafficEstimate](../adinsight-api/trafficestimate-data-object.md), [KeywordIdea](../adinsight-api/keywordidea-data-object.md), and more.|
|[Ad Insight Error Data Objects](../adinsight-api/ad-insight-error-data-objects.md)|Be sure to [handle](~/concepts/handling-service-errors-and-exceptions.md) errors, for example [OperationError](../adinsight-api/operationerror-data-object.md) would be returned if the user credentials cannot be authenticated.|
|[Ad Insight Value Sets](../adinsight-api/ad-insight-value-sets.md)|Value sets include [BidOpportunityType](../adinsight-api/bidopportunitytype-value-set.md), [KeywordOpportunityType](../adinsight-api/keywordopportunitytype-value-set.md), and [TargetAdPosition](../adinsight-api/targetadposition-value-set.md). You'll also find value sets for supported budget limit type, currency, and more.|

## See Also
[Getting Started With the Bing Ads API](~/concepts/getting-started-with-the-https://msdn.microsoft.com/library/bing-ads-api.md)  
[Bing Ads Technical Guides](~/concepts/bing-ads-technical-guides.md)  
[Bing Ads Web Service Addresses](~/concepts/bing-ads-web-service-addresses.md)  
[Bing Ads API Error Codes](~/concepts/bing-ads-operation-error-codes.md)  

