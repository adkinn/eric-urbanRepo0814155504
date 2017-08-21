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
|[AdGroupBidLandscape](../adinsight-api/adgroupbidlandscape-data-object.md)|Defines an object that contains a list of estimated clicks, cost, and impressions from 1 to 7 days for the ad group given the suggested bid.|
|[AdGroupBidLandscapeInput](../adinsight-api/adgroupbidlandscapeinput-data-object.md)|Defines an object that contains the requested bid landscape type for the corresponding ad group identifier.|
|[AdGroupEstimate](../adinsight-api/adgroupestimate-data-object.md)|Contains a list of suggested keywords for the ad group with minimum and maximum traffic estimates. Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|
|[AdGroupEstimator](../adinsight-api/adgroupestimator-data-object.md)|Contains a list of keyword estimators with your keyword level filter criteria for traffic estimates.|
|[BidLandscapePoint](../adinsight-api/bidlandscapepoint-data-object.md)|Defines an object that contains estimates of clicks, cost, and impressions  given the suggested bid.|
|[BidOpportunity](../adinsight-api/bidopportunity-data-object.md)|Defines an object that contains the suggested bid with estimated clicks and impressions opportunities.|
|[BroadMatchKeywordOpportunity](../adinsight-api/broadmatchkeywordopportunity-data-object.md)|Defines an object that contains the marketplace impact statistics of including broad match type keyword bids.|
|[BroadMatchSearchQueryKPI](../adinsight-api/broadmatchsearchquerykpi-data-object.md)|Defines an object that contains search query statistics of including broad match type keyword bids.|
|[BudgetOpportunity](../adinsight-api/budgetopportunity-data-object.md)|Defines an object that contains the suggested budget with estimated clicks and impressions opportunities. Additionally, the object contains a list of budget points with weekly  impressions, clicks and cost estimates for the given budget amount.|
|[BudgetPoint](../adinsight-api/budgetpoint-data-object.md)|Defines an object that contains a budget amount and an estimate of weekly impressions, clicks, and cost for this budget amount.|
|[CampaignEstimate](../adinsight-api/campaignestimate-data-object.md)|Contains a nested list of suggested keywords for the campaign's ad groups with minimum and maximum traffic estimates. Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|
|[CampaignEstimator](../adinsight-api/campaignestimator-data-object.md)|Contains campaign filter criteria and a nested list of ad group and keyword level filter criteria for traffic estimates.|
|[CategorySearchParameter](../adinsight-api/categorysearchparameter-data-object.md)|The keyword category search parameter that you can use as a seed for new keyword ideas.|
|[CompetitionSearchParameter](../adinsight-api/competitionsearchparameter-data-object.md)|The competition search parameter filter that you can include when requesting keyword ideas.|
|[Criterion](../adinsight-api/criterion-data-object.md)|This is the base class from which keyword planner criterion objects derive.|
|[DateRangeSearchParameter](../adinsight-api/daterangesearchparameter-data-object.md)|The date range search parameter that you can include when requesting keyword ideas.|
|[DayMonthAndYear](../adinsight-api/daymonthandyear-data-object.md)|Defines an object that you use to specify the start and end dates of a date range.|
|[DeviceCriterion](../adinsight-api/devicecriterion-data-object.md)|The device criterion that you can include when requesting keyword ideas or traffic estimates.|
|[DeviceSearchParameter](../adinsight-api/devicesearchparameter-data-object.md)|The device search parameter filter that you can include when requesting keyword ideas.|
|[DomainCategory](../adinsight-api/domaincategory-data-object.md)|Defines an object that contains a domain category with website coverage.|
|[EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md)|Defines an object that contains estimates of clicks, average cost per click (CPC), impressions, click-through rate (CTR), and total cost for the specified keyword given the suggested bid.|
|[EstimatedPositionAndTraffic](../adinsight-api/estimatedpositionandtraffic-data-object.md)|Defines an object that contains the estimated search results position and estimated keyword statistics such as clicks, average cost per click (CPC), impressions, click-through rate (CTR), and total cost for the specified keyword given the specified bid.|
|[ExcludeAccountKeywordsSearchParameter](../adinsight-api/excludeaccountkeywordssearchparameter-data-object.md)|The exclude account keywords search parameter filter that you can include when requesting keyword ideas.|
|[HistoricalSearchCountPeriodic](../adinsight-api/historicalsearchcountperiodic-data-object.md)|Defines an object that contains the number of times that the keyword was used in a search query during the specified time period.|
|[IdeaTextSearchParameter](../adinsight-api/ideatextsearchparameter-data-object.md)|The idea text search parameter filter that you can include when requesting keyword ideas.|
|[ImpressionShareSearchParameter](../adinsight-api/impressionsharesearchparameter-data-object.md)|The impression share search parameter filter that you can include when requesting keyword ideas.|
|[Keyword](../adinsight-api/keyword-data-object.md)|Defines a keyword with match type.|
|[KeywordAndConfidence](../adinsight-api/keywordandconfidence-data-object.md)|Defines an object that contains a suggested keyword and a confidence score that indicates the level of confidence in the keyword that would result in the URL (from which the keyword came) being included in the search results.|
|[KeywordAndMatchType](../adinsight-api/keywordandmatchtype-data-object.md)|Defines an object that contains suggested match types for the keyword.|
|[KeywordBidLandscape](../adinsight-api/keywordbidlandscape-data-object.md)|Defines an object that contains a list of estimated clicks, cost, and impressions from 1 to 7 days for the keyword identifier given the suggested bid.|
|[KeywordCategory](../adinsight-api/keywordcategory-data-object.md)|Defines an object that contains a keyword category and a confidence score. The confidence score indicates the likelihood that the keyword belongs to the keyword category.|
|[KeywordCategoryResult](../adinsight-api/keywordcategoryresult-data-object.md)|Defines an object that contains the keyword and a list of keyword categories that the keyword might belong to.|
|[KeywordDemographic](../adinsight-api/keyworddemographic-data-object.md)|Defines an object that contains the device, age and gender of the user who entered the search query, if known.|
|[KeywordDemographicResult](../adinsight-api/keyworddemographicresult-data-object.md)|Defines an object that contains the keyword and percentage of users by age and gender (if known) who searched for the specified keyword.|
|[KeywordEstimate](../adinsight-api/keywordestimate-data-object.md)|A suggested keyword with minimum and maximum traffic estimates. Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|
|[KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md)|Defines an object that contains the keyword and the suggested bid value for each match type.|
|[KeywordEstimatedPosition](../adinsight-api/keywordestimatedposition-data-object.md)|Defines an object that contains the keyword and the estimated position in the search results for each match type.|
|[KeywordEstimator](../adinsight-api/keywordestimator-data-object.md)|Contains a keyword estimators with your keyword level filter criteria for traffic estimates.|
|[KeywordHistoricalPerformance](../adinsight-api/keywordhistoricalperformance-data-object.md)|Defines an object that contains the key performance index data for the specified keyword.|
|[KeywordIdea](../adinsight-api/keywordidea-data-object.md)|Defines an object that contains a suggested keyword with historical statistics, like monthly search volume, competition, suggested minimum bid, and ad impression share.|
|[KeywordIdeaCategory](../adinsight-api/keywordideacategory-data-object.md)|Defines an object that contains a keyword idea category.|
|[KeywordIdEstimatedBid](../adinsight-api/keywordidestimatedbid-data-object.md)|Defines an object that contains the identifier of the keyword and the suggested bid value for the keyword and match type.|
|[KeywordIdEstimatedPosition](../adinsight-api/keywordidestimatedposition-data-object.md)|Defines an object that contains the identifier of a keyword and the estimated search results position for the keyword and match type.|
|[KeywordKPI](../adinsight-api/keywordkpi-data-object.md)|Defines a key performance index object for a keyword. The object contains the historical performance statistics of the keyword for the corresponding match type, ad position, and device.|
|[KeywordLocation](../adinsight-api/keywordlocation-data-object.md)|Defines an object that contains the location, device, and the percentage of time that a user entered a search query.|
|[KeywordLocationResult](../adinsight-api/keywordlocationresult-data-object.md)|Defines an object that contains the locations where users were located when they searched for the specified keyword.|
|[KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md)|Defines an object that contains a suggested keyword and bid value.|
|[KeywordSearchCount](../adinsight-api/keywordsearchcount-data-object.md)|Defines an object that contains a list of search counts for each device where the keyword was included in a search query. The data is aggregated based on the attributes specified in the request.|
|[KeywordSuggestion](../adinsight-api/keywordsuggestion-data-object.md)|Defines an object that contains a list of suggested keywords that could perform better than the specified keyword.|
|[LanguageCriterion](../adinsight-api/languagecriterion-data-object.md)|The language criterion that you can include when requesting keyword ideas or traffic estimates.|
|[LanguageSearchParameter](../adinsight-api/languagesearchparameter-data-object.md)|The language search parameter filter that you can include when requesting keyword ideas.|
|[LocationCriterion](../adinsight-api/locationcriterion-data-object.md)|The location criterion that you can include when requesting keyword ideas or traffic estimates.|
|[LocationSearchParameter](../adinsight-api/locationsearchparameter-data-object.md)|The location search parameter filter that you can include when requesting keyword ideas.|
|[NegativeKeyword](../adinsight-api/negativekeyword-data-object.md)|Defines a negative keyword with match type.|
|[NetworkCriterion](../adinsight-api/networkcriterion-data-object.md)|The network criterion that you can include when requesting keyword ideas or traffic estimates.|
|[NetworkSearchParameter](../adinsight-api/networksearchparameter-data-object.md)|The network search parameter filter that you can include when requesting keyword ideas.|
|[Opportunity](../adinsight-api/opportunity-data-object.md)|This is the base class from which opportunity objects derive. The class contains the key used to identify the opportunity and the date by when the opportunity expires.|
|[QuerySearchParameter](../adinsight-api/querysearchparameter-data-object.md)|The query search parameter that you can use as a seed for new keyword ideas.|
|[SearchCountsByAttributes](../adinsight-api/searchcountsbyattributes-data-object.md)|Defines an object that contains a list of keyword historical search counts for the corresponding device attribute. Each search count in the list is aggregated by day, month, and year.|
|[SearchParameter](../adinsight-api/searchparameter-data-object.md)|This is the base class from which keyword idea search parameter objects derive. |
|[SearchVolumeSearchParameter](../adinsight-api/searchvolumesearchparameter-data-object.md)|The search volume search parameter filter that you can include when requesting keyword ideas.|
|[SuggestedBidSearchParameter](../adinsight-api/suggestedbidsearchparameter-data-object.md)|The suggested bid search parameter filter that you can include when requesting keyword ideas.|
|[TrafficEstimate](../adinsight-api/trafficestimate-data-object.md)|Defines an object that contains traffic estimates based on the campaign, ad group, and keyword criteria you specified when calling [GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md).|
|[UrlSearchParameter](../adinsight-api/urlsearchparameter-data-object.md)|The URL search parameter that you can use as a seed for new keyword ideas.|
