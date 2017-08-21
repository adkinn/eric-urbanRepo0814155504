---
title: "Budget and Bid Opportunities"
ms.custom: ""
ms.date: "08/09/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01c7f611-4f35-4b5d-aeee-027bbc985aeb
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Budget and Bid Opportunities
The [Ad Insight](~/adinsight-api/ad-insight-service-reference.md) service is a keyword research service that you can use to research keyword, bid, and budget opportunities:

-   Get past keyword performance.  
-   Get the estimated minimum keyword bid that may result in ads appearing in the specified search results position.  
-   Get the estimated position where ads may appear given the specified bid.  
-   Get suggested relevant keywords from the content of a web page or from other keywords.  
-   Get the locations and demographics (age and gender) of the users who have searched for specified keywords.  
-   Discover opportunities for improving the performance of your advertising campaigns. The results are similar to using the opportunities tab of the [!INCLUDE[brand](../concepts/includes/brand.md)] web application.  

You can get most of this information broken out by device type.

Some operations, such as [GetHistoricalKeywordPerformance](~/adinsight-api/gethistoricalkeywordperformance-service-operation.md), let you request data for multiple countries. For information about how the data is aggregated when you specify multiple countries, see [Aggregating Data](#aggregate).

The Ad Insight operations are grouped into the following categories.

-   [Campaign Budget Opportunities](#campaignopportunities)  
-   [Ad Group Bid Opportunities](#adgroupopportunities)  
-   [Keyword Bid Opportunities](#keywordopportunities)  
-   [Keyword Research and Opportunities](#keywordresearch)  
-   [Aggregating Data](#aggregate)  

## <a name="campaignopportunities"></a>Campaign Budget Opportunities
To identify campaigns that have been paused or are in jeopardy of being paused due to budget-related issues, call the [GetBudgetOpportunities](~/adinsight-api/getbudgetopportunities-service-operation.md) operation. The response contains a list of [BudgetOpportunity](~/adinsight-api/budgetopportunity-data-object.md) objects that recommends a budget, which may increase the campaign’s clicks and impressions and decrease the chance of the campaign being paused for budget-related reasons. Each [BudgetOpportunity](~/adinsight-api/budgetopportunity-data-object.md) contains a list of [BudgetPoint](~/adinsight-api/budgetpoint-data-object.md) objects. You can use the budget points to compare your current budget to any of the proposed budgets.

## <a name="adgroupopportunities"></a>Ad Group Bid Opportunities
Given a list of existing ad groups, the [GetBidLandscapeByAdGroupIds](~/adinsight-api/getbidlandscapebyadgroupids-service-operation.md) operation returns for each a list of suggested bids and estimated performance statistics. You can use the landscape view of multiple bid points with estimated traffic for the same ad group to help make decisions about how to adjust your ad group level default bid to optimize for clicks, impressions, and cost. For example you might use the resulting data to visualize a clicks to cost curve or a bid to impressions curve.

## <a name="keywordopportunities"></a>Keyword Bid Opportunities
You can use these operations to optimize bids for existing keywords.

-   Given a list of existing keywords, the [GetBidLandscapeByKeywordIds](~/adinsight-api/getbidlandscapebykeywordids-service-operation.md) operation returns for each a list of suggested bids and estimated performance statistics. You can use the landscape view of multiple bid points with estimated traffic for the same keyword to help make decisions about how to adjust your keyword bid to optimize for clicks, impressions, and cost. For example you might use the resulting data to visualize a clicks to cost curve or a bid to impressions curve. For more information, see the help article [View impression and cost estimates before changing your bid](http://help.bingads.microsoft.com/#apex/3/en/51096/1).

-   To identify which keyword’s performance may be improved with minimal increase in cost per click, call the [GetBidOpportunities](~/adinsight-api/getbidopportunities-service-operation.md) operation. The response contains a list of [BidOpportunity](~/adinsight-api/bidopportunity-data-object.md) objects that suggest a bid value that may increase clicks and impressions while minimally increasing costs.

-   To get the minimum suggested bid value of one or more keywords that could result in an ad appearing in the targeted position in the search results, call the [GetEstimatedBidByKeywords](~/adinsight-api/getestimatedbidbykeywords-service-operation.md) or [GetEstimatedBidByKeywordIds](~/adinsight-api/getestimatedbidbykeywordids-service-operation.md) operation. You can use the estimates of clicks, average cost per click (CPC), and impressions that the keywords could generate based on the suggested bid price to determine whether the cost of landing in that position is worth the possible traffic it could generate. The difference between the two operations is that [GetEstimatedBidByKeywords](~/adinsight-api/getestimatedbidbykeywords-service-operation.md) factors in how well the keyword performed among all advertisers in the specified publisher countries, while [GetEstimatedBidByKeywordIds](~/adinsight-api/getestimatedbidbykeywordids-service-operation.md) factors in how well the keyword performed in the ad group.

-   To get the estimated position in the search results if the specified keywords use the specified bid value, call the [GetEstimatedPositionByKeywords](~/adinsight-api/getestimatedpositionbykeywords-service-operation.md) or [GetEstimatedPositionByKeywordIds](~/adinsight-api/getestimatedpositionbykeywordids-service-operation.md) operation. You can use the estimated position, clicks, average cost per click (CPC), and impressions that the keywords could generate based on the bid price to determine if you need to bid more or less to achieve the desired position and whether the cost of landing in that position is worth the possible traffic it could generate. The difference between the two operations is that [GetEstimatedPositionByKeywords](~/adinsight-api/getestimatedpositionbykeywords-service-operation.md) factors in how well the keyword performed among all advertisers in the specified publisher countries, while [GetEstimatedPositionByKeywordIds](~/adinsight-api/getestimatedpositionbykeywordids-service-operation.md) factors in how well the keyword performed in the ad group.

-   To get the historical performance (bid and traffic) of one or more keywords used in search queries, call the [GetHistoricalKeywordPerformance](~/adinsight-api/gethistoricalkeywordperformance-service-operation.md) operation. You can use the information to gauge the historical cost of bidding on the keyword and the traffic it generated.

## <a name="keywordresearch"></a>Keyword Research and Opportunities
You can use these operations to discover new keywords.

-   To identify new keywords that are relevant to an ad group, call the [GetKeywordOpportunities](~/adinsight-api/getkeywordopportunities-service-operation.md) operation. The response includes [KeywordOpportunity](~/adinsight-api/keywordopportunity-data-object.md) objects that contain the suggested keyword, exact-match bid value and the estimated monthly volume of user search queries that exactly matches the keyword. Applying the opportunity adds the keyword to the ad group.

-   To get the age and gender of users who have searched for specific keywords, call the [GetKeywordDemographics](~/adinsight-api/getkeyworddemographics-service-operation.md) operation. The operation returns the demographics information broken out by device type. You can use the information to target your ads to device types with the most reach and to boost your bid for users of a specific gender and age group.

-   To get a count of the number of search queries that included the specified keywords, call the [GetHistoricalSearchCount](~/adinsight-api/gethistoricalsearchcount-service-operation.md) operation. You can use the information to gauge the competitive strength of the keyword and to make sure that you are bidding on keywords that users are using.

-   To get the geographical location of users who have searched for specific keywords, call the [GetKeywordLocations](~/adinsight-api/getkeywordlocations-service-operation.md) operation. You can request that locations be shown at country, state, metropolitan, or city level. The operation returns the location information broken out by device type. You can use the information to target your ads to device types with the most reach and to locations with the most searches for the keyword.

-   To get keyword suggestions for your web page, call the [SuggestKeywordsForUrl](~/adinsight-api/suggestkeywordsforurl-service-operation.md) operation.

-   To get keyword suggestions that could perform better than the specified keywords, call the [SuggestKeywordsFromExistingKeywords](~/adinsight-api/suggestkeywordsfromexistingkeywords-service-operation.md) operation. You can specify the type of keywords that the operation suggests. For example, you can request keywords from other ad groups that include the specified keyword or request search queries that contain keywords that are related to the specified keyword.

-   The [GetKeywordCategories](~/adinsight-api/getkeywordcategories-service-operation.md) operation can be used to get the categories of your specified keywords.

## <a name="aggregate"></a>Aggregating Data
For operations that provide historical performance such as [GetHistoricalKeywordPerformance](~/adinsight-api/gethistoricalkeywordperformance-service-operation.md), you can request data for multiple publisher countries. If you specify multiple countries, the data is aggregated across the countries. If you set *PublisherCountries* to NULL, the data is aggregated across all countries that support the specified language.

For example, if you set *Language* to English and *PublisherCountries* to NULL, the [GetHistoricalKeywordPerformance](~/adinsight-api/gethistoricalkeywordperformance-service-operation.md) operation will set the *AverageBid* value to the maximum bid specified across all countries that support English. However, the other KPI values, such as *Clicks*, will be set to the sum of those values across all the countries that support English.

Likewise, if you set *Language* to English and *PublisherCountries* to a list of countries, the [GetHistoricalKeywordPerformance](~/adinsight-api/gethistoricalkeywordperformance-service-operation.md) operation will set the *AverageBid* value to the maximum bid specified across the countries and set the other KPI values, such as *Clicks*, to the sum of those values across the specified countries.

If your goal is to compete successfully in a country, you should specify only that country. Specifying a single country will provide more appropriate bid information for that country. If you specify multiple countries, the bid will be the highest bid across all countries, which could result in overbidding in some countries. However, if your goal is to get the historical cost of doing business in multiple countries in order to plan your budget, you should specify all the countries that your campaign will target.

For operations that provide estimates, such as [GetEstimatedBidByKeywords](~/adinsight-api/getestimatedbidbykeywords-service-operation.md), you can request data for multiple publisher countries but the behavior is different in the case where *PublisherCountries* is NULL. In this case, instead of aggregating the data across all countries, the response calculates results using data from the country with the most impressions.

For operations that suggest keywords, such as [SuggestKeywordsFromExistingKeywords](~/adinsight-api/suggestkeywordsfromexistingkeywords-service-operation.md), the behavior is the same as that of operations that provide historical performance.

## See Also
[Ad Insight Service Reference](~/adinsight-api/ad-insight-service-reference.md)  
[Bing Ads Web Service Addresses](../concepts/bing-ads-web-service-addresses.md)  

