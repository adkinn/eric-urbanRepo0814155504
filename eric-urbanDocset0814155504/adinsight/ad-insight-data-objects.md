---
title: "Ad Insight Data Objects"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fab2ec06-0ea6-4a43-b590-f6e2540f2705
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Insight Data Objects
The Ad Insight service defines the following data objects.

|Data Object|Description|
|---------------|---------------|
|[AdGroupBidLandscape](../Ad Insight Version 11/adgroupbidlandscape-data-object.md)|Defines an object that contains a list of estimated clicks, cost, and impressions from 1 to 7 days for the ad group given the suggested bid.|
|[AdGroupBidLandscapeInput](../Ad Insight Version 11/adgroupbidlandscapeinput-data-object.md)|Defines an object that contains the requested bid landscape type for the corresponding ad group identifier.|
|[AdGroupEstimate](../Ad Insight Version 11/adgroupestimate-data-object.md)|Contains a list of suggested keywords for the ad group with minimum and maximum traffic estimates. Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|
|[AdGroupEstimator](../Ad Insight Version 11/adgroupestimator-data-object.md)|Contains a list of keyword estimators with your keyword level filter criteria for traffic estimates.|
|[BidLandscapePoint](../Ad Insight Version 11/bidlandscapepoint-data-object.md)|Defines an object that contains estimates of clicks, cost, and impressions  given the suggested bid.|
|[BidOpportunity](../Ad Insight Version 11/bidopportunity-data-object.md)|Defines an object that contains the suggested bid with estimated clicks and impressions opportunities.|
|[BroadMatchKeywordOpportunity](../Ad Insight Version 11/broadmatchkeywordopportunity-data-object.md)|Defines an object that contains the marketplace impact statistics of including broad match type keyword bids.|
|[BroadMatchSearchQueryKPI](../Ad Insight Version 11/broadmatchsearchquerykpi-data-object.md)|Defines an object that contains search query statistics of including broad match type keyword bids.|
|[BudgetOpportunity](../Ad Insight Version 11/budgetopportunity-data-object.md)|Defines an object that contains the suggested budget with estimated clicks and impressions opportunities. Additionally, the object contains a list of budget points with weekly  impressions, clicks and cost estimates for the given budget amount.|
|[BudgetPoint](../Ad Insight Version 11/budgetpoint-data-object.md)|Defines an object that contains a budget amount and an estimate of weekly impressions, clicks, and cost for this budget amount.|
|[CampaignEstimate](../Ad Insight Version 11/campaignestimate-data-object.md)|Contains a nested list of suggested keywords for the campaign's ad groups with minimum and maximum traffic estimates. Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|
|[CampaignEstimator](../Ad Insight Version 11/campaignestimator-data-object.md)|Contains campaign filter criteria and a nested list of ad group and keyword level filter criteria for traffic estimates.|
|[CategorySearchParameter](../Ad Insight Version 11/categorysearchparameter-data-object.md)|The keyword category search parameter that you can use as a seed for new keyword ideas.|
|[CompetitionSearchParameter](../Ad Insight Version 11/competitionsearchparameter-data-object.md)|The competition search parameter filter that you can include when requesting keyword ideas.|
|[Criterion](../Ad Insight Version 11/criterion-data-object.md)|This is the base class from which keyword planner criterion objects derive.|
|[DateRangeSearchParameter](../Ad Insight Version 11/daterangesearchparameter-data-object.md)|The date range search parameter that you can include when requesting keyword ideas.|
|[DayMonthAndYear](../Ad Insight Version 11/daymonthandyear-data-object.md)|Defines an object that you use to specify the start and end dates of a date range.|
|[DeviceCriterion](../Ad Insight Version 11/devicecriterion-data-object.md)|The device criterion that you can include when requesting keyword ideas or traffic estimates.|
|[DeviceSearchParameter](../Ad Insight Version 11/devicesearchparameter-data-object.md)|The device search parameter filter that you can include when requesting keyword ideas.|
|[DomainCategory](../Ad Insight Version 11/domaincategory-data-object.md)|Defines an object that contains a domain category with website coverage.|
|[EstimatedBidAndTraffic](../Ad Insight Version 11/estimatedbidandtraffic-data-object.md)|Defines an object that contains estimates of clicks, average cost per click (CPC), impressions, click-through rate (CTR), and total cost for the specified keyword given the suggested bid.|
|[EstimatedPositionAndTraffic](../Ad Insight Version 11/estimatedpositionandtraffic-data-object.md)|Defines an object that contains the estimated search results position and estimated keyword statistics such as clicks, average cost per click (CPC), impressions, click-through rate (CTR), and total cost for the specified keyword given the specified bid.|
|[ExcludeAccountKeywordsSearchParameter](../Ad Insight Version 11/excludeaccountkeywordssearchparameter-data-object.md)|The exclude account keywords search parameter filter that you can include when requesting keyword ideas.|
|[HistoricalSearchCountPeriodic](../Ad Insight Version 11/historicalsearchcountperiodic-data-object.md)|Defines an object that contains the number of times that the keyword was used in a search query during the specified time period.|
|[IdeaTextSearchParameter](../Ad Insight Version 11/ideatextsearchparameter-data-object.md)|The idea text search parameter filter that you can include when requesting keyword ideas.|
|[ImpressionShareSearchParameter](../Ad Insight Version 11/impressionsharesearchparameter-data-object.md)|The impression share search parameter filter that you can include when requesting keyword ideas.|
|[Keyword](../Ad Insight Version 11/keyword-data-object.md)|Defines a keyword with match type.|
|[KeywordAndConfidence](../Ad Insight Version 11/keywordandconfidence-data-object.md)|Defines an object that contains a suggested keyword and a confidence score that indicates the level of confidence in the keyword that would result in the URL (from which the keyword came) being included in the search results.|
|[KeywordAndMatchType](../Ad Insight Version 11/keywordandmatchtype-data-object.md)|Defines an object that contains suggested match types for the keyword.|
|[KeywordBidLandscape](../Ad Insight Version 11/keywordbidlandscape-data-object.md)|Defines an object that contains a list of estimated clicks, cost, and impressions from 1 to 7 days for the keyword identifier given the suggested bid.|
|[KeywordCategory](../Ad Insight Version 11/keywordcategory-data-object.md)|Defines an object that contains a keyword category and a confidence score. The confidence score indicates the likelihood that the keyword belongs to the keyword category.|
|[KeywordCategoryResult](../Ad Insight Version 11/keywordcategoryresult-data-object.md)|Defines an object that contains the keyword and a list of keyword categories that the keyword might belong to.|
|[KeywordDemographic](../Ad Insight Version 11/keyworddemographic-data-object.md)|Defines an object that contains the device, age and gender of the user who entered the search query, if known.|
|[KeywordDemographicResult](../Ad Insight Version 11/keyworddemographicresult-data-object.md)|Defines an object that contains the keyword and percentage of users by age and gender (if known) who searched for the specified keyword.|
|[KeywordEstimate](../Ad Insight Version 11/keywordestimate-data-object.md)|A suggested keyword with minimum and maximum traffic estimates. Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|
|[KeywordEstimatedBid](../Ad Insight Version 11/keywordestimatedbid-data-object.md)|Defines an object that contains the keyword and the suggested bid value for each match type.|
|[KeywordEstimatedPosition](../Ad Insight Version 11/keywordestimatedposition-data-object.md)|Defines an object that contains the keyword and the estimated position in the search results for each match type.|
|[KeywordEstimator](../Ad Insight Version 11/keywordestimator-data-object.md)|Contains a keyword estimators with your keyword level filter criteria for traffic estimates.|
|[KeywordHistoricalPerformance](../Ad Insight Version 11/keywordhistoricalperformance-data-object.md)|Defines an object that contains the key performance index data for the specified keyword.|
|[KeywordIdea](../Ad Insight Version 11/keywordidea-data-object.md)|Defines an object that contains a suggested keyword with historical statistics, like monthly search volume, competition, suggested minimum bid, and ad impression share.|
|[KeywordIdeaCategory](../Ad Insight Version 11/keywordideacategory-data-object.md)|Defines an object that contains a keyword idea category.|
|[KeywordIdEstimatedBid](../Ad Insight Version 11/keywordidestimatedbid-data-object.md)|Defines an object that contains the identifier of the keyword and the suggested bid value for the keyword and match type.|
|[KeywordIdEstimatedPosition](../Ad Insight Version 11/keywordidestimatedposition-data-object.md)|Defines an object that contains the identifier of a keyword and the estimated search results position for the keyword and match type.|
|[KeywordKPI](../Ad Insight Version 11/keywordkpi-data-object.md)|Defines a key performance index object for a keyword. The object contains the historical performance statistics of the keyword for the corresponding match type, ad position, and device.|
|[KeywordLocation](../Ad Insight Version 11/keywordlocation-data-object.md)|Defines an object that contains the location, device, and the percentage of time that a user entered a search query.|
|[KeywordLocationResult](../Ad Insight Version 11/keywordlocationresult-data-object.md)|Defines an object that contains the locations where users were located when they searched for the specified keyword.|
|[KeywordOpportunity](../Ad Insight Version 11/keywordopportunity-data-object.md)|Defines an object that contains a suggested keyword and bid value.|
|[KeywordSearchCount](../Ad Insight Version 11/keywordsearchcount-data-object.md)|Defines an object that contains a list of search counts for each device where the keyword was included in a search query. The data is aggregated based on the attributes specified in the request.|
|[KeywordSuggestion](../Ad Insight Version 11/keywordsuggestion-data-object.md)|Defines an object that contains a list of suggested keywords that could perform better than the specified keyword.|
|[LanguageCriterion](../Ad Insight Version 11/languagecriterion-data-object.md)|The language criterion that you can include when requesting keyword ideas or traffic estimates.|
|[LanguageSearchParameter](../Ad Insight Version 11/languagesearchparameter-data-object.md)|The language search parameter filter that you can include when requesting keyword ideas.|
|[LocationCriterion](../Ad Insight Version 11/locationcriterion-data-object.md)|The location criterion that you can include when requesting keyword ideas or traffic estimates.|
|[LocationSearchParameter](../Ad Insight Version 11/locationsearchparameter-data-object.md)|The location search parameter filter that you can include when requesting keyword ideas.|
|[NegativeKeyword](../Ad Insight Version 11/negativekeyword-data-object.md)|Defines a negative keyword with match type.|
|[NetworkCriterion](../Ad Insight Version 11/networkcriterion-data-object.md)|The network criterion that you can include when requesting keyword ideas or traffic estimates.|
|[NetworkSearchParameter](../Ad Insight Version 11/networksearchparameter-data-object.md)|The network search parameter filter that you can include when requesting keyword ideas.|
|[Opportunity](../Ad Insight Version 11/opportunity-data-object.md)|This is the base class from which opportunity objects derive. The class contains the key used to identify the opportunity and the date by when the opportunity expires.|
|[QuerySearchParameter](../Ad Insight Version 11/querysearchparameter-data-object.md)|The query search parameter that you can use as a seed for new keyword ideas.|
|[SearchCountsByAttributes](../Ad Insight Version 11/searchcountsbyattributes-data-object.md)|Defines an object that contains a list of keyword historical search counts for the corresponding device attribute. Each search count in the list is aggregated by day, month, and year.|
|[SearchParameter](../Ad Insight Version 11/searchparameter-data-object.md)|This is the base class from which keyword idea search parameter objects derive. |
|[SearchVolumeSearchParameter](../Ad Insight Version 11/searchvolumesearchparameter-data-object.md)|The search volume search parameter filter that you can include when requesting keyword ideas.|
|[SuggestedBidSearchParameter](../Ad Insight Version 11/suggestedbidsearchparameter-data-object.md)|The suggested bid search parameter filter that you can include when requesting keyword ideas.|
|[TrafficEstimate](../Ad Insight Version 11/trafficestimate-data-object.md)|Defines an object that contains traffic estimates based on the campaign, ad group, and keyword criteria you specified when calling [GetKeywordTrafficEstimates](../Ad Insight Version 11/getkeywordtrafficestimates-service-operation.md).|
|[UrlSearchParameter](../Ad Insight Version 11/urlsearchparameter-data-object.md)|The URL search parameter that you can use as a seed for new keyword ideas.|
