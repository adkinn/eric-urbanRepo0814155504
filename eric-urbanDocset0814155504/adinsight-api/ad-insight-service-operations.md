---
title: "Ad Insight Service Operations"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdc436f7-fca7-43be-afa2-5f5b997dd525
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Insight Service Operations
The Ad Insight service defines the following service operations.

|Service Operation|Description|Request Limits|
|---------------------|---------------|------------------|
|[GetBidLandscapeByAdGroupIds](../adinsight-api/getbidlandscapebyadgroupids-service-operation.md)|Given a list of existing ad groups, this operation returns for each a list of suggested bids and estimated performance statistics. You can use the landscape view of multiple bid points with estimated traffic for the same ad group to help make decisions about how to adjust your ad group level default bid to optimize for clicks, impressions, and cost. For example you might use the resulting data to visualize a clicks to cost curve or a bid to impressions curve.|1,000 *AdGroupBidLandscapeInput*|
|[GetBidLandscapeByKeywordIds](../adinsight-api/getbidlandscapebykeywordids-service-operation.md)|Given a list of existing keywords, this operation returns for each a list of suggested bids and estimated performance statistics from 1 to  7 days. This operation is not based on target position, rather it returns multiple bid options that yield different estimated clicks, impressions, and cost. You can use the landscape view of multiple bid points with estimated traffic for the same keyword to help make decisions about how to adjust your keyword bid to optimize for clicks, impressions, and cost. For example you might use the resulting data to visualize a clicks to cost curve or a bid to impressions curve. |1,000 *KeywordIds*|
|[GetBidOpportunities](../adinsight-api/getbidopportunities-service-operation.md)|Gets the keyword bid opportunities of the specified ad group.|1 *AdGroupId*<br />1 *CampaignId*|
|[GetBudgetOpportunities](../adinsight-api/getbudgetopportunities-service-operation.md)|Gets the campaign budget opportunities of the specified account.|1 *CampaignId*|
|[GetDomainCategories](../adinsight-api/getdomaincategories-service-operation.md)|Gets the list of categories available for the website domain and language.|1 *DomainName*<br/>1 *Language*|
|[GetEstimatedBidByKeywordIds](../adinsight-api/getestimatedbidbykeywordids-service-operation.md)|Gets the estimated bid value of one or more keywords - specified by keyword identifier - that could have resulted in an ad appearing in the targeted position in the search results.|1,000 *KeywordIds*|
|[GetEstimatedBidByKeywords](../adinsight-api/getestimatedbidbykeywords-service-operation.md)|Gets the estimated bid value of one or more keywords that could result in an ad appearing in the targeted position in the search results.|1 *AdGroupId*<br />1,000 *Keywords*|
|[GetEstimatedPositionByKeywordIds](../adinsight-api/getestimatedpositionbykeywordids-service-operation.md)|Gets the estimated position in the search results if the specified bid value had been used for the keywords - specified by keyword identifier.|1,000 *KeywordIds*|
|[GetEstimatedPositionByKeywords](../adinsight-api/getestimatedpositionbykeywords-service-operation.md)|Gets the estimated position in the search results if the specified bid value would be used for the specified keywords.|1 *AdGroupId*<br />1,000 *Keywords*|
|[GetHistoricalKeywordPerformance](../adinsight-api/gethistoricalkeywordperformance-service-operation.md)|Gets the historical performance of the normalized search term.|1,000 *Keywords*|
|[GetHistoricalSearchCount](../adinsight-api/gethistoricalsearchcount-service-operation.md)|Gets the number of times the normalized term was used in a search during the specified time period.|1,000 *Keywords*|
|[GetKeywordCategories](../adinsight-api/getkeywordcategories-service-operation.md)|Gets the keyword categories to which the specified keywords belong.|1,000 *Keywords*<br />5 *MaxCategories*|
|[GetKeywordDemographics](../adinsight-api/getkeyworddemographics-service-operation.md)|Gets the age and gender of users who have searched for the specified keywords.|1,000 *Keywords*|
|[GetKeywordIdeaCategories](../adinsight-api/getkeywordideacategories-service-operation.md)|Gets the list of keyword idea categories.|Not applicable|
|[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)|Gets a list of keyword ideas.<br/><br/>Suggests new ad groups and keywords based on your existing keywords, website, and product category. You can also request historical statistics for keywords e.g., monthly searches, competition, average CPC, and ad impression share. You can use the returned suggested keyword bids as input to the [GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md) operation.|Maximum 1 of each [SearchParameter](../adinsight-api/searchparameter-data-object.md) type within *SearchParameters*|
|[GetKeywordLocations](../adinsight-api/getkeywordlocations-service-operation.md)|Gets the geographical locations of users who have searched for the specified keywords.|1,000 *Keywords*<br />10 *MaxLocations*|
|[GetKeywordOpportunities](../adinsight-api/getkeywordopportunities-service-operation.md)|Gets a list of keyword opportunities that are relevant to the specified ad group. The keyword opportunity also includes a suggested bid value.|1 *AdGroupId*<br />1 *CampaignId*|
|[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)|Provides traffic estimates for keywords e.g., average CPC, average position, clicks, CTR, impressions, and total cost. As input you provide the bid, language, location, and network, with optional campaign budget and negative keyword filters. |1 *Campaigns*|
|[SuggestKeywordsForUrl](../adinsight-api/suggestkeywordsforurl-service-operation.md)|Suggests the possible keywords for the content located at the specified URL.|200 *MaxKeywords*<br />1 *Url*|
|[SuggestKeywordsFromExistingKeywords](../adinsight-api/suggestkeywordsfromexistingkeywords-service-operation.md)|Suggests keywords that could perform better than the specified keywords.|1,000 *Keywords*<br />100 *MaxSuggestionsPerKeyword*|
