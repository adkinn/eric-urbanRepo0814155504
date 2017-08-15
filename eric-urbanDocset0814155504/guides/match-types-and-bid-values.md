---
title: "Match Types and Bid Values"
ms.custom: na
ms.date: "07/20/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 55e7e664-a4c3-4ed7-8433-081fa3900f20
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
robots: noindex,nofollow
---
# Match Types and Bid Values
 Before your ads can run, you need to set your campaign’s budget. You'll also need to choose a bid strategy type, and optionally set keyword level match type bids. Depending on the type of campaign you are running, see the following sections for more details.

|Exact Match Bid Value|Campaign Types|
|-------------------------|--------------------------|
|[Budget Types](#budgettypes)|All|
|[Bid Strategy Types](#bidstrategytypes)|SearchAndContent<br/>DynamicSearchAds|
|[Keyword Match Types](#keywordmatchtypes)|SearchAndContent|

## <a name="budgettypes"></a>Budget Types
Your budget tells Bing Ads how much you want to spend on your campaign. You can set a daily budget for each campaign and when you reach your budget, Bing Ads will stop displaying your ads until the next day or month. Keep your advertising costs under control by keeping track of your budget. 

With shared budgets you can set a single daily budget that can be used by any campaign within the same account. This enables you to efficiently distribute a single daily budget across all campaigns or across a defined group of campaigns within your Bing Ads account. 

> [!IMPORTANT]
> To avoid a breaking change when updating campaigns, you might need to code for shared budgets in the Bing Ads platform, even if you do not plan to use shared budgets. For more details and to determine whether the campaign uses a shared budget, check the value of the *BudgetId* element ([Campaign](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaign.aspx) object) or *Budget Id* field (Bulk ([Campaign](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-record.aspx) object) record).

The Bing Ads API supports the *DailyBudgetAccelerated* and *DailyBudgetStandard* values as defined in the [BudgetLimitType](https://msdn.microsoft.com/library/bing-ads-campaign-management-budgetlimittype.aspx) value set.

### <a name="dailyaccelerated"></a>DailyBudgetAccelerated
Show your ads for every relevant search, spending at an accelerated rate until you run out of budget for the day. When the daily budget limit is reached, your ads will stop displaying until the next calendar day.

Consider using this option if you want your ads to show more frequently earlier in the day until your budget is reached, to maximize the number of impressions.

### <a name="dailystandard"></a>DailyBudgetStandard
Show your ads evenly every day throughout the month so you don’t run out of budget early in the month. If the click rate is higher than expected, the rate of spend may be slowed to ensure that the budget is available until the end of the day; however, you won’t exceed the estimated monthly budget.

This is a great option if you have a limited budget and want your ads to show evenly throughout the day. This way, your ads won’t show all at once in the morning, using up your limited budget early in the day. You will also be able to monitor your budget on a daily basis, making adjustments as necessary, to maximize your budget.


## <a name="bidstrategytypes"></a>Bid Strategy Types
Your bid strategy setting tells Bing Ads how you want to manage your bids. Whichever bid strategy you use, Bing Ads will always respect your budget limit. 

> [!NOTE]
> The Bing Ads web application uses the term *Bid strategy*, the Bing Ads Bulk API uses the *Bid Strategy Type* column for upload and download, and the Bing Ads Campaign Management API derives several bid strategy objects from the [BiddingScheme](https://msdn.microsoft.com/library/bing-ads-campaign-management-biddingscheme.aspx) object.

The following bid strategy types are available per campaign:

|Bid Strategy Type|Campaign Types|
|-------------------------|--------------------------|
|[ManualCpc](#manualcpc)|All|
|[MaxClicks](#maxclicks)|SearchAndContent<br/>DynamicSearchAds|
|[MaxConversions](#maxconversions)|SearchAndContent<br/>DynamicSearchAds|
|[EnhancedCpc](#enhancedcpc)|SearchAndContent<br/>DynamicSearchAds|
|[TargetCpa](#targetcpa)|SearchAndContent<br/>DynamicSearchAds|

> [!IMPORTANT] 
> The *MaxClicks*, *MaxConversions*, and *TargetCpa* bid strategy types will be available to pilot participants from late Q2 through early Q3 calendar 2017. You should be prepared for the new bid strategy types if you or a pilot participant might use your application. If the campaign bid strategy type is set to *MaxClicks*, *MaxConversions*, or *TargetCpa*, the behavior of existing features will change unless you set an individual ad group’s or keyword’s bid strategy to *ManualCpc*. 
> -  You can continue to set the ad group and keyword bids; however they will not be used by Bing Ads.
> -  Bing Ads will periodically change your stored ad group or keyword bid settings. You can continue to set new bids, however Bing Ads may change them at any type using this bid strategy type.
> -  You can continue to set bid adjustments e.g. for age, gender, or location; however with one exception they will not be used by Bing Ads. Bing Ads will not honor any bid adjustments, unless you have set a bid adjustment of -100% (opt out).
> -  Whether you chose the *DailyBudgetAccelerated* or *DailyBudgetStandard* budget type, Bing Ads will use the *DailyBudgetStandard* budget type. 
> 
> Also note that you must have conversion tracking (a UET tag and a conversion goal) set up for the *EnhancedCpc*, *MaxConversions*, and *TargetCpa* bid strategy types to work. See [Universal Event Tracking](../guides/universal-event-tracking.md) for more information.
> 
> To set the *MaxConversions* or *TargetCpa* bid strategy types, the campaign must have at least 15 conversions in the last 30 days. If you try to add or update a campaign to use one of these strategy types, the requested operation will fail if there is not enough conversion history. If an active campaign uses one of these bid strategy types, and then ceases to meet the minimum conversion history requirement at any time, Bing Ads will stop auto bidding but will continue to use the *DailyBudgetStandard* budget type. For a new campaign we recommend that you start with *EnhancedCpc* and then when the campaign has enough conversion history, you can update it to use either the *MaxConversions* or *TargetCpa* bid strategy.

> [!TIP] 
> You can set your campaign’s bid strategy to *EnhancedCpc*, *MaxClicks*, *MaxConversions*, or *TargetCpa* and then, at any time, set an individual ad group’s or keyword’s bid strategy to *ManualCpc*.

### <a name="manualcpc"></a>ManualCpc
With the *ManualCpc* (manual cost per click) bid strategy, you set your ad group and keyword bids, and Bing Ads uses these bids every time. This is every campaign's default bid strategy unless you chose a different strategy when creating your campaign. 

### <a name="maxclicks"></a>MaxClicks
With the *MaxClicks* bid strategy, Bing Ads automatically sets your bids with the goal of getting as many clicks as possible with your provided budget.

### <a name="maxconversions"></a>MaxConversions
With the *MaxConversions* bid strategy, Bing Ads automatically sets your bids with the goal of getting as many conversions as possible with your provided budget. 

### <a name="enhancedcpc"></a>EnhancedCpc
With the *EnhancedCpc* (enhanced cost per click) bid strategy, you set your ad group and keyword bids, and Bing Ads automatically adjusts your bids in real time to increase your chances for a conversion. When we see a good opportunity, we increase your bid up to 30% to capitalize on it. On the other hand, if the patterns show that a conversion is less likely, we lower your bid as low as -100% i.e. will not bid on it. Up or down, this change will be made after we apply any bid adjustments you have set. If you haven't optimized your campaign yet, Enhanced CPC should reduce your cost per conversion and increase your total conversion count while respecting your current budget.

Differing from the *MaxClicks*, *MaxConversions*, and *TargetCpa* bid strategies, with the *EnhancedCpc* bid strategy, Bing Ads will not actually change your stored ad group or keyword bid settings. You can continue to set new bids, and we will use the new values as a starting point next opportunity; however, assuming the *EnhancedCpc* bid strategy remains in place, we will continue to modify the new bid from negative 100% through positive 30%.

### <a name="targetcpa"></a>TargetCpa
With the *TargetCpa* bid strategy, Bing Ads automatically sets your bids such that the target average CPA (cost per acquisition) is attained. 

## <a name="keywordmatchtypes"></a>Keyword Match Types
Match type bids help [!INCLUDE[brand](../guides/includes/brand.md)] determine how closely you want a search term or other input to match your keyword. The keyword that you bid on is compared to the user’s search term in the order of *Exact*, *Phrase*, and then *Broad*.

### <a name="exactmatchtype"></a>Exact
An exact match results when all of the words in the keyword exactly match the user's search term.

If the plural form is not in your keyword list, the plural form of a keyword is also used in an exact match comparison. For example, if you specify an exact-match bid for the keyword, *car*, both *car* and *cars* will match. To prevent plural form of a keyword from matching, add the plural form to the campaign or ad group’s negative keyword list.

If your keyword list does not contain the plural form of the keyword, all search results for the plural form will be included in the singular form of the keyword in the keyword performance report.

### <a name="phrasematchtype"></a>Phrase
A phrase match results when all of the words in the keyword phrase are present in the user's search term and are in the same order. For example, the keyword phrase "red flower" will match the search term "big red flower" and "red flower", but not "yellow or blue flower" or "flower red".

### <a name="broadmatchtype"></a>Broad
A broad match results when words in the keyword phrase are present in the user's search term; however, the order of the words can vary. For example, the keyword *red flower* will match the search term *red flower*, *flower is red*, and other variations. It will also match the query *red* and the query *flower*.

Broad match can also match on synonyms and other semantic variations of the queries. For example, a search term for *red carnation* might result in your ad being displayed because carnation is a type of flower.
    
Because the search engine can vary its algorithms to expand queries to find broader matches by looking for synonyms and other meanings of the queries, the outcome can sometimes result in keywords being matched to irrelevant queries.

To reduce the chance of irrelevant ads being served to users and the quality score of those ads being affected due to low CTR, you can add any irrelevant queries to your list of negative keywords. To determine the irrelevant queries, see the [Report Types](../guides/report-types.md).

You can also use the broad match modifier to require that specific terms in your keyword be present in the search term. To implement the broad match modifier, include a plus sign (+) in front of every term in the keyword that must be present in the search term. For example, if you bid on “Hawaii hotels”, your ad could be served for the search queries, “Hawaii beach hotels” and “Hawaii rentals.” However, if you changed the keyword to “+Hawaii +hotel”, the keyword would match only “Hawaii beach hotels.”

If you include the broad match modifier on a keyword that specifies a phrase or exact match-type bid, the plus sign will be treated as part of the keyword and not as a modifier.

### <a name="deliveredmatchtypes"></a>Bid and Delivered Match Types
You should set the ad group *Search Bid* that will be used as the default bid for *Exact*, *Phrase*, and *Broad* match types. You can then override the default by setting individual keyword level match types. Generally, the more precise you require the match to be, the higher conversion rates tend to be while impressions tend to decrease. Finding the right balance between conversions and impressions can help maximize the return on investment (ROI) of your campaign. If you're not sure which match type to use, we suggest starting with broad match. You can then use keyword performance reports over time to see which keywords lead to ad clicks and optimize your keyword list.
-   If a majority of the keywords in the report are not related to your ad, you might want to use one of the more precise match types.  
-   For keywords that you want to continue leading to clicks, add them to your keyword list with a more specific match type such as Phrase or Exact.  
-   For keywords that you don't want leading to clicks, add them to your keyword list as negative keywords. For more information, see [Negative Keywords](../guides/negative-keywords.md).  

Exact match is the most restrictive and broad match is the least restrictive match type. If the keyword matches by using the more restrictive match type, it will also match using the less restrictive match types. If the exact match comparison succeeds, the exact-match bid value is used if it exists; otherwise, it gets the bid value from the first less-restrictive match type that has a bid value (set at the keyword or ad group level).

If there is not an exact match, the phrase-match type comparison is used. If there is a match, the phrase-match bid value is used if it exists; otherwise, the broad-match bid value is used (set at the keyword broad match bid or ad group level search bid). If there is not a phrase match, the broad-match type comparison is used. If there is a match, the broad-match bid value is used (set at the keyword broad match bid or ad group level search bid).

The following table shows example keyword bid values for each match type, as well as the bid value that would be used based on the delivered match type if the keyword participated in the auction. The delivered match type (exact, phrase, or broad) identifies the comparison used to match the keyword to the user’s query. For example, if the keyword is “red shoes” and the user’s query is “pretty red shoes,” the delivered match type would be phrase. The delivered match type may differ from the match type you bid, for example if you bid on a broad match and the search term was an exact match.

|Exact Match Bid Value|Phrase Match Bid Value|Broad Match Bid Value|Delivered Match Type|Bid Value Used|
|-------------------------|--------------------------|-------------------------|------------------------|------------------|
|No bid|0.10|0.20|Exact|0.10|
|No bid|0.20|0.10|Exact|0.20|
|No bid|No bid|0.10|Exact|0.10|
|No bid|No bid|0.10|Phrase|0.10|
|0.10|0.30|0.20|Exact|0.10|
|0.10|0.30|0.20|Phrase|0.30|
|0.20|No bid|No bid|Exact|0.20|
|0.20|No bid|No bid|Phrase|None. Would not participate in auction.|

## See Also
[Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md)

