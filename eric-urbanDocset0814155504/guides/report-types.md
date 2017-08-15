---
title: "Report Types"
ms.custom: na
ms.date: "07/10/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: ecc8ff48-0818-4001-a8a0-a78eaa6c471d
caps.latest.revision: 16
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Report Types
The reporting service provides reports that you can use to track finances, measure ad performance, and adjust settings to optimize your budget or campaign. The service supports the majority of popular reports available in the [!INCLUDE[brand](../guides/includes/brand.md)] web application.

Each report type aggregates the data at a different level or with a different focus. For example, you can get the performance data broken out at the keyword level, which is the lowest level of aggregation for a search campaign; or you get the performance data rolled up to the account level, which is the highest level of aggregation. You should expect a keyword performance report to take longer to generate than an account performance report.

The reports that you can request are grouped into the following categories.

-   [Performance](#performance)  
-   [Ad Extensions](#adextensions)  
-   [Product Ads](#productads)  
-   [Dynamic Search Ads](#dynamicsearchads)  
-   [Change History](#changehistory)  
-   [Targeting](#targeting)  
-   [Campaign Analytics](#analytics)  
-   [Billing and Budget](#budget)  

## <a name="performance"></a>Performance
Delivery performance reports show the overall effectiveness and cost of ads and keywords for a specified time period. Most of the reports include a similar set of performance statistics, for example impressions, clicks, and click-through rate. The optional attributes are a strong factor in distinguishing which report to use. For example the ad performance, ad dynamic text performance, and destination URL performance reports all provide similar ad performance data, each with a different set of attributes. 

You would use the account and campaign performance reports to monitor click and spend data to ensure that you are optimizing your budget, and you would use the ad and keyword performance reports to identify ads and keywords that are performing well in terms of click-through rate and conversions.

|Report|Description|
|----------|---------------|
|[AccountPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-accountperformancereportrequest.aspx)|Use this report to observe long-term account performance and trends.<br /><br />You can request impressions, impression share (%), clicks, spend, and average cost per click for individual accounts. Once downloaded, this data can be sorted by individual accounts, currency, bid match type, and delivered match type.|
|[AdDynamicTextPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-addynamictextperformancereportrequest.aspx)|Use this report to identify which dynamic text strings are performing well and which strings you should consider changing.<br /><br />You can request impressions, clicks, spend, and average cost per click of your dynamic text strings. Once downloaded, this data can be sorted by ad title, destination URL, param 1, param 2, and param 3.|
|[AdGroupPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportrequest.aspx)|Use this report to more broadly compare delivery performance statistics by ad group, campaign, or account attributes rather than at the keyword level.<br /><br />You can request impressions, impression share (%), clicks, spend, and average cost per click of your ad groups. Once downloaded, this data can be sorted by ad group, ad group status, language, and network.|
|[AdPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adperformancereportrequest.aspx)|Use this report to help you determine which ads lead to clicks and conversions, and which are not performing. Having underperforming ads in your account can pull down the quality of your campaigns.<br /><br />You can request impressions, clicks, spend, and average cost per click for each ad. Once downloaded, this data can be sorted by ad ID, ad status, ad title, display URL, and destination URL.|
|[AudiencePerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-audienceperformancereportrequest.aspx)|Use this report to compare delivery performance statistics by audience, ad group, campaign, or account attributes.<br /><br />You can request impressions, clicks, spend, and average cost per click. Once downloaded, this data can be sorted by audience, association status, ad group, and targeting setting.|
|[CampaignPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportrequest.aspx)|Use this report to view high-level performance statistics and quality attributes for each campaign or account. This is also a quick way to flag any major campaign or account problems.<br /><br />You can request impressions, impression share (%), clicks, spend, and average cost per click for each campaign or account. Once downloaded, this data can be sorted by campaign, campaign status, and quality score.|
|[DestinationUrlPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-destinationurlperformancereportrequest.aspx)|Use this report to identify landing pages that met audience expectations and potentially resulted in high click-through or conversion rates.<br /><br />You can request impressions, clicks, spend, and average cost per click for your landing pages. Once downloaded, this data can be sorted by destination URL, account, campaign, and ad group.|
|[KeywordPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportrequest.aspx)|Use this report to find out which keywords are performing well and those that are not.<br /><br />You can request impressions, clicks, spend, and average cost per click for your landing pages. Once downloaded, this data can be sorted by keyword, account, campaign, and ad group.|
|[PublisherUsagePerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-publisherusageperformancereportrequest.aspx)|Use this report to see if any website URLs aren’t performing well enough for your campaign or ad group target settings. For example, if ad impressions at those URLs yield a low click-through rate, then you might decide to exclude those websites from your campaign.<br /><br />You can request impressions, clicks, spend, and conversions for websites including the [!INCLUDE[brand](../guides/includes/brand.md)] and syndicated search partner networks. Once downloaded, this data can be sorted by website URL, account, campaign, and ad group.|
|[SearchQueryPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-searchqueryperformancereportrequest.aspx)|Use this report to see what your audience is searching for when your ads are shown. You can use this information to make informed additions, removals, or edits to both your keyword and negative keyword lists.<br /><br />You can request impressions, clicks, click-through rate, and average position for search terms that have triggered your ads.<br /><br />For example, if you are a mortgage lender who is running a campaign with the following keywords: mortgage, home mortgage, and home equity loans; and the report shows that the search query “mortgage rates” results in many impressions of your ad, you would probably add “rates” to your keyword list. However, if you do not provide reverse mortgages and the report shows that the search query “reverse mortgage” results in many impressions, you would probably add “reverse mortgage” to your negative keywords list.|
|[ShareOfVoiceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-shareofvoicereportrequest.aspx)|Use this report to view impression share (%) of successful bids for each keyword, and identify opportunities to increase impression share.<br /><br />You can request impressions, impression share (%), impression share lost to budget (%), and impression share lost to bid. Once downloaded, this data can be sorted by keyword, keyword ID, landing page user experience, and quality score.|

## <a name="adextensions"></a>Ad Extensions
Ad extension reports give you a closer look at how each ad extension is performing based on click type for ads and keywords and ad extension properties for ad groups.

|Report|Description|
|----------|---------------|
|[AdExtensionByAdReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adextensionbyadreportrequest.aspx)|Use this report to compare how well different versions of your ad extensions are performing with each ad.<br /><br />You can request impressions, clicks, spend, and average cost per click by ad. Once downloaded, this data can be sorted by ad ID, ad title, ad extension type, and ad extension version.|
|[AdExtensionByKeywordReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adextensionbykeywordreportrequest.aspx)|Use this report to compare how well different versions of your ad extensions are performing for each keyword.<br /><br />You can request impressions, clicks, spend, and average cost per click of your extensions for each keyword. Once downloaded, this data can be sorted by keyword, keyword ID, ad extension type, and ad extension version.|
|[AdExtensionDetailReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adextensiondetailreportrequest.aspx)|Use this report to discover the effectiveness of individual ad extension items, for example each link of a sitelink extension.<br /><br />You can request impressions, clicks, spend, and average cost per click of individual extension items. Once downloaded, this data can be sorted by the individual ad extension display name, ad extension ID, and ad extension type.|
|[CallDetailReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-calldetailreportrequest.aspx)|Use this report to discover which accounts, campaigns, or ad groups are driving the most completed phone calls.<br /><br />You can request duration and phone spend for each forwarded call that originated from a call ad extension.|


## <a name="productads"></a>Product Ads
Product ad reports give you a closer look at how your Bing Shopping Campaigns are performing based on product partition and product offer data.

|Report|Description|
|----------|---------------|
|[ProductDimensionPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productdimensionperformancereportrequest.aspx)|Use this report to find out which product dimensions are performing well and those that are not.<br /><br />You can request impressions, clicks, spend, and average cost per click for your landing pages. Once downloaded, this data can be sorted by product category, custom label, title, and type.|
|[ProductPartitionPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportrequest.aspx)|Use this report to find out which product partitions are performing well and those that are not.<br /><br />You can request impressions, clicks, spend, and average cost per click for your landing pages. Once downloaded, this data can be sorted by product group and product partition type.|
|[ProductPartitionUnitPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionunitperformancereportrequest.aspx)|Use this report to find out which product partition units are performing well and those that are not.<br /><br />You can include details in the report such as impressions, clicks, and spend that you can use to identify whether or not the product partitions are performing well. Once downloaded, this data can be sorted by product group.|
|[ProductSearchQueryPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productsearchqueryperformancereportrequest.aspx)|Use this report to get insight into what your audience is searching for when your ads are shown as well as ensure that your product titles are relevant to search queries.<br /><br />You can request impressions, clicks, and click-through rate based on the search terms that have triggered your ads. Once downloaded, this data can be sorted by product, account, campaign, and ad group.|

## <a name="dynamicsearchads"></a>Dynamic Search Ads
Dynamic search ad reports give you a closer look at how your Dynamic Search Ads are performing based on dynamic ad target data.

|Report|Description|
|----------|---------------|
|[DSAAutoTargetPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-dsaautotargetperformancereportrequest.aspx)|Use this report to find out which DSA auto targets are performing well and those that are not.<br /><br />You can request impressions, clicks, click-through rate, and average position for the dynamic ad targets that have triggered your ads. Once downloaded, this data can be sorted by dynamic ad target.|
|[DSACategoryPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-dsacategoryperformancereportrequest.aspx)|Use this report to find out which DSA categories are performing well and those that are not.<br /><br />You can request impressions, clicks, click-through rate, and average position for the DSA categories that have triggered your ads. Once downloaded, this data can be sorted by device and DSA category.|
|[DSASearchQueryPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-dsasearchqueryperformancereportrequest.aspx)|Use this report to find out which search terms are in demand for your DSA campaign and the performance of dynamic headlines that are being displayed.<br /><br />You can request impressions, clicks, click-through rate, and average position for the search queries that have triggered your ads. Once downloaded, this data can be sorted by search query, headline, category list, and dynamic ad target.|

## <a name="changehistory"></a>Change History

|Report|Description|
|----------|---------------|
|[SearchCampaignChangeHistoryReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-searchcampaignchangehistoryreportrequest.aspx)|Use this report to discover when changes to an account were made, as well as which user made the changes.<br /><br />You can request a record of changes made by user and date. For example, you can request a record of changes to campaign name, location target association, and keyword bid. You can request both the old value and new value in the report.|

## <a name="targeting"></a>Targeting
You can use the targeting reports to determine whether your ads are reaching their intended audiences.

|Report|Description|
|----------|---------------|
|[AgeGenderDemographicReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-agegenderdemographicreportrequest.aspx)|Use this report to discover how your campaigns and ad groups are resonating with audiences of diverse age and gender.<br /><br />You can request impression rate (%) and click-through-rate (%) for each campaign or ad group, organized by gender and age group.|
|[GeographicPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-geographicperformancereportrequest.aspx)|Use this report to see which locations your traffic is coming from. You can then validate whether your location targeting strategy is successful, and identify opportunities to improve. The report also identifies either the physical location of the search user or the geographical location interest based on the user’s search query.<br /><br />You can request impressions, clicks, spend, and average cost per click for each ad group, organized by city, country, metro area, radius, state, and account.|
|[NegativeKeywordConflictReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-negativekeywordconflictreportrequest.aspx)|Use this report to discover which keywords and negative keywords are in conflict, and whether the conflict is at the campaign or ad group level. Use this list to figure out which negative keywords to delete.<br /><br />You can request negative keywords that conflict with some of your keywords, and block your ad from showing.|
|[UserLocationPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-userlocationperformancereportcolumn.aspx)|Use this report to see which locations your traffic is coming from. You can then validate whether your location targeting strategy is successful, and identify opportunities to improve. The report also identifies the physical location of the user and the intended geographical location of the user’s search query, for example a user in Seattle searching for services in Portland.<br /><br />You can request impressions, clicks, spend, and average cost per click for each ad group, organized by city, country, metro area, radius, state, and account.|


## <a name="analytics"></a>Campaign Analytics
If you enable account analytics, you can use the conversion tracking data to measure the effectiveness of the account’s ad campaigns, primarily in terms of return on investment. In addition, you can use the reports to learn which pages on your website are most commonly abandoned by visitors and then use this information to change the design of your website to improve conversions.

[!INCLUDE[available_with_analytics](../guides/includes/available_with_analytics.md)]

|Report|Description|
|----------|---------------|
|[ConversionPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-conversionperformancereportrequest.aspx)|Use this report to understand which campaigns and keywords are leading an audience to complete a purchase or other conversion action.<br /><br />You can request conversions, assists, revenue, and revenue per conversion for your campaigns. Once downloaded, this data can be sorted by account, ad group, campaign, keyword, and device type.|
|[GoalsAndFunnelsReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-goalsandfunnelsreportrequest.aspx)|Use this report to discover whether your audience completes each step through the land, browse, prospect, and conversion pages of your website. For example, you can use this report to determine the step that users leave the conversion funnel, so that you can improve or remove that step to increase the chance that the user will continue to the next step.<br /><br />You can request spend, revenue, assists, conversions, and conversion steps of your websites. Once downloaded, this data can be sorted by account, ad group, campaign, keyword, and goal.|


## <a name="budget"></a>Billing and Budget

|Report|Description|
|----------|---------------|
|[BudgetSummaryReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-budgetsummaryreportrequest.aspx)|Use this report to discover how your campaign’s budget is performing for the month. For example, the report shows your monthly budget, how much you have spent to date, and whether you are on target to spend your monthly budget.<br /><br />You can request your monthly budget, how much you have spent to date, and whether you are on target to spend your monthly budget.|


