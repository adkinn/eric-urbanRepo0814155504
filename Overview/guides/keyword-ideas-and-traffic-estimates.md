---
title: "Keyword Ideas and Traffic Estimates"
ms.custom: na
ms.date: "08/09/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 91a9b52f-33ad-4ad6-b1bb-b6f61d156838
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
---
# Keyword Ideas and Traffic Estimates
Choosing keywords is one of the most important aspects of creating and maintaining a successful advertising campaign. But where to start? How do you identify the many possible keywords that describe your business? How much should you bid on those keywords to be competitive with other advertisers?

This guide describes how you can discover [keyword ideas](#keywordideas) and [traffic estimates](#keywordtrafficestimates) for your search advertising campaigns with the the [Ad Insight](https://msdn.microsoft.com/library/bing-ads-ad-insight-service-reference.aspx) service. The results are similar to using the Keyword Planner tool in the [!INCLUDE[brand](../guides/includes/brand.md)] web application. For additional keyword research, campaign budget opportunities, and ad group bid opportunities, see [Bid and Budget Opportunities](../guides/budget-and-bid-opportunities.md). 

> [!NOTE]
> Keyword Planner features are currently available to customers in the United States, United Kingdom, Canada, Australia, France, and Germany.

## <a name="keywordideas"></a>Keyword Ideas
Given a list of existing keywords, the [GetKeywordIdeas](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordideas.aspx) operation suggests new ad groups and keywords based on your existing keywords, website, and product category. You can also request historical statistics for keywords e.g., monthly searches, competition, average CPC, and ad impression share. You can use the returned suggested keyword bids as input to the [GetKeywordTrafficEstimates](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordtrafficestimates.aspx) operation.

With the Bing Ads web application's Keyword Planner tool you search for new keywords using a phrase, website, or category as shown in the screen shot below.
 
![GetKeywordIdeas to Keyword Planner UI](../guides/media/getkeywordideas-to-keyword-planner-ui.png)

Likewise with the [GetKeywordIdeas](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordideas.aspx) operation you must specify one or more of the corresponding search parameters.
-  The [QuerySearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-querysearchparameter.aspx) corresponds to filling in *Product or service*.
-  The [UrlSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-urlsearchsearchparameter.aspx) corresponds to filling in *Your landing page*.
-  The [CategorySearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-categorysearchparameter.aspx) corresponds to filling in *Your product category*. To get a list of keyword category identifiers, use the [GetKeywordIdeaCategories](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordideacategories.aspx) service operation.

With the Bing Ads web application's Keyword Planner tool you can refine the search for example, by location, language, network, and negative keywords. Likewise with the [GetKeywordIdeas](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordideas.aspx) operation you must specify all of these search parameters: [LanguageSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-languagesearchparameter.aspx), [LocationSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-locationsearchparameter.aspx), and [NetworkSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-networksearchparameter.aspx). 

Each of the [CompetitionSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-competitionsearchparameter.aspx), [DateRangeSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-daterangesearchparameter.aspx), [ExcludeAccountKeywordsSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-excludeaccountkeywordssearchparameter.aspx), [IdeaTextSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-ideatextsearchparameter.aspx), [ImpressionShareSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-impressionsharesearchparameter.aspx), [SearchVolumeSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-searchvolumesearchparameter.aspx), and [SuggestedBidSearchParameter](https://msdn.microsoft.com/library/bing-ads-ad-insight-suggestedbidsearchparameter.aspx) are optional. Use these search options to refine what keywords we suggest. You can limit the keywords by historical data, hide keywords already in your account, and include or exclude specific keywords.

The result is a [KeywordIdea](https://msdn.microsoft.com/library/bing-ads-ad-insight-keywordidea.aspx) list. Each keyword idea includes historical statistics for keywords e.g., monthly searches, competition, average CPC, and ad impression share. Whereas the Bing Ads web application returns a 12 month average of the historical monthly search counts, each [KeywordIdea](https://msdn.microsoft.com/library/bing-ads-ad-insight-keywordidea.aspx) includes a list of monthly search counts. You can use each count individually or average them for parity with the Bing Ads web application's calculation.

## <a name="keywordtrafficestimates"></a>Keyword Traffic Estimates
Once you have already settled on an initial set of keywords, the [GetKeywordTrafficEstimates](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordtrafficestimates.aspx) operation provides traffic estimates for keywords e.g., average CPC, average position, clicks, CTR, impressions, and total cost. As input you provide the keyword, bid, language, location, and network, with optional campaign budget and negative keyword filters.

With the Bing Ads web application's Keyword Planner tool under *Get performance and cost estimates* you are prompted to either enter keywords or upload a file with keywords. The [GetKeywordTrafficEstimates](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordtrafficestimates.aspx) operation requires that you already have a list of keywords e.g., retrieved via the [GetKeywordIdeas](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordideas.aspx) operation. 

![GetKeywordTrafficEstimates to Keyword Planner UI](../guides/media/getkeywordtrafficestimates-to-keyword-planner-ui.png)

The following inputs are required for the [GetKeywordTrafficEstimates](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordtrafficestimates.aspx) operation.
-  In the *Criteria* element of the [CampaignEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-campaignestimator.aspx) object you must specify all of these criteria: [LanguageCriterion](https://msdn.microsoft.com/library/bing-ads-ad-insight-languagecriterion.aspx), [LocationCriterion](https://msdn.microsoft.com/library/bing-ads-ad-insight-locationcriterion.aspx), and [NetworkCriterion](https://msdn.microsoft.com/library/bing-ads-ad-insight-networkcriterion.aspx).
- In the *AdGroupEstimators* element of the [CampaignEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-campaignestimator.aspx) object you must include one or more [AdGroupEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-adgroupestimator.aspx) objects. Each [AdGroupEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-adgroupestimator.aspx) must include one or more [KeywordEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-keywordestimator.aspx) objects. Each [KeywordEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-keywordestimator.aspx) object must contain the keyword text and match type.

The following inputs are optional for the [GetKeywordTrafficEstimates](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordtrafficestimates.aspx) operation.
- Include exactly one [DeviceCriterion](https://msdn.microsoft.com/library/bing-ads-ad-insight-devicecriterion.aspx) in the *Criteria* element of the [CampaignEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-campaignestimator.aspx) object if you want to filter the results for one device. If you do not specify a device, the returned traffic estimates are aggregated for all devices.
- Include *DailyBudget* with the [CampaignEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-campaignestimator.aspx) object if you want to constrain the results given a specific campaign daily budget.
- Include *NegativeKeywords* with the [CampaignEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-campaignestimator.aspx) object if you want to filter the results by specific negative keywords.
- Include *MaxCpc* with the [AdGroupEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-adgroupestimator.aspx) object if you want to get the results with a specific ad group bid setting.
- Include *MaxCpc* with the [KeywordEstimator](https://msdn.microsoft.com/library/bing-ads-ad-insight-keywordestimator.aspx) object if you want to get the results with a specific keyword bid setting.

The result is a [KeywordEstimate](https://msdn.microsoft.com/library/bing-ads-ad-insight-keywordestimate.aspx) list for each [AdGroupEstimate](https://msdn.microsoft.com/library/bing-ads-ad-insight-adgroupestimate.aspx), which are all nested within one [CampaignEstimate](https://msdn.microsoft.com/library/bing-ads-ad-insight-campaignestimate.aspx). Each keyword estimate includes a minimum and maximum [TrafficEstimate](https://msdn.microsoft.com/library/bing-ads-ad-insight-trafficestimate.aspx). As previously mentioned, the traffic estimates for keywords include average CPC, average position, clicks, CTR, impressions, and total cost.

## See Also
[Ad Insight Service Reference](https://msdn.microsoft.com/library/bing-ads-ad-insight-service-reference.aspx)  
[Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md)  
