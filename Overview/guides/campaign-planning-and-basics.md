---
title: "Campaign Planning and Basics"
ms.custom: na
ms.date: "08/12/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 138b72fb-2d2e-44e3-b752-b0f6c16e6433
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
---
# Campaign Planning and Basics
The [!INCLUDE[brand](../guides/includes/brand.md)] API provides access to all of your campaign settings, including ads, keywords, ad extensions, and targets. For an introduction to the account and campaign hierarchy within a customer, see [Entity Hierarchy and Limits](../guides/entity-hierarchy-and-limits.md).

One or more advertising campaigns can be created within a [!INCLUDE[brand](../guides/includes/brand.md)] account. Before you can add a campaign, you must know the identifier of the account that you want to add the campaign to. Typically, when you create an account, you store the account identifier locally because you often have to refer to it. However, to get the account identifier if you do not store it locally, call the [GetAccountsInfo](https://msdn.microsoft.com/library/dn451289.aspx) operation using the [Customer Management Service](https://msdn.microsoft.com/library/bb671848.aspx). Note that your campaign must adhere to the [Budget Rules](#budget_rules).

One or more ad groups can be created within a campaign. You'll want to give these ad groups meaningful names and keep them tightly focused with related keywords and a small number of ads, for example 3 ads per ad group. If you do not specify default bid values for the ad group, the ad group will use default bid values based on the currency of the account, and pricing model, and the bidding model. For more information, see [Budget and Bid Strategies](../guides/budget-and-bid-strategies.md). To change the ad rotation behavior of rotating the best performing ads to rotating all ads in the ad group evenly, set the ad group's ad rotation property. For more information, see [Rotating Ads](#rotation).

To advertise with a text ad you should bid on keywords in a *Search and Content* campaign. For text ads the combination of the ad’s title, text, and display URL must be unique for all ads within an ad group. You can extend the ad layout to be more visually appealing and feature rich using [Product Ads and Bing Shopping Campaigns](../Topic/Product%20Ads%20and%20Bing%20Shopping%20Campaigns.md). To advertise in a *Shopping* campaign with a product ad from your [!INCLUDE[storebrand](../guides/includes/storebrand.md)] store, you should bid using campaign and ad group criterion which filters ads from your store. For product ads, the promotional text must be unique for all ads within an ad group. For more information, see [Product Ads and Bing Shopping Campaigns](../Topic/Product%20Ads%20and%20Bing%20Shopping%20Campaigns.md).

You can specify the landing page URL where a user is directed when your ad is clicked. In [!INCLUDE[brand](../guides/includes/brand.md)] the landing page URLs are typically referred to as Final URLs. Global parameters, custom parameters, and tracking templates are optional features that you can use for advanced management of your landing page URLs. For more information, see [URL Tracking with Upgraded URLs](../guides/url-tracking-with-upgraded-urls.md). Dynamic parameters are used to customize the ad at display time, for example to reflect the user’s search term. Using dynamic parameters can help increase the ad’s click-through rate (CTR). For more information, see the Bing Ads help articles [What tracking or URL parameters can I use?](http://go.microsoft.com/fwlink/?LinkId=785078) and [Automatically customize your ads with dynamic text parameters](http://go.microsoft.com/fwlink/?LinkId=785080).

Finally for Search and Content campaigns, take a look at the keywords you've created for your ad group. Are they all closely related? Do you want to add any others? Are you using a mix of match types? Consider using the [Ad Insight Service](https://msdn.microsoft.com/library/bing-ads-ad-insight-service-reference.aspx) to get ideas for additional keywords you might want to include in this ad group, and for suggested starting bids. For more information, see [Budget and Bid Opportunities](../guides/budget-and-bid-opportunities.md). You should create a keyword for each match type that you want to bid on. For example, to bid on exact-match and phrase-match for the keyword *car*, you must create two Keyword objects. When you add the keywords, you’ll get a unique keyword ID for each keyword and match-type combination. For details on specifying a bid amount, see [Budget and Bid Strategies](../guides/budget-and-bid-strategies.md). Keep in mind that you cannot change a keyword’s match type from one match-type bid to another match-type bid. For example, you cannot update a keyword from exact match to phrase match. Instead, you must add a new keyword that specifies a bid amount for the new match type. Optionally you may delete the original keyword if you do not want to bid on its match type.

You should also be aware of *keyword normalization*, which is the process by which extraneous characters such as punctuation marks are removed from keywords, negative keywords, and customer queries. Normalizing keywords and queries allows more user search queries to match your keywords, thus potentially increasing ad coverage. Knowing which characters are removed can help you make your keywords more effective. For more information, see [Keyword Normalization](#normalization). You can also use negative keywords to prevent you ads from being served if the user’s search query contains one of your negative keywords. For more information about negative keywords, see [Negative Keywords](../guides/negative-keywords.md).

Before an ad can be served, all related entities must pass editorial review. For more information, see [Editorial Review and Appeals](../guides/editorial-review-and-appeals.md).

You can show your ads to customers in specific locations, like cities or countries, to users of a certain age group or gender, or to display at a certain day and time of the week. These target settings can be set for each campaign and ad group. For more information about showing ads to your target audience, see [Show Ads to Your Target Audience](../guides/show-ads-to-your-target-audience.md).

You can manage advertising campaign settings with either the [Bulk Service](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference.aspx) or [Campaign Management Service](https://msdn.microsoft.com/library/bing-ads-campaign-management-service-reference.aspx). You should use the [Bulk Service](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference.aspx) if you need to upload or download a high volume of entity settings. For example you can update all keyword bids for your entire account in a single upload. In comparison, with the [Campaign Management Service](https://msdn.microsoft.com/library/bing-ads-campaign-management-service-reference.aspx) you can only update 1,000 keywords per call and those keywords must be in the same ad group. For details see the following sections.

-   [Managing Advertising Settings with the Bulk Service](#bulkservice)  
-   [Managing Advertising Settings with the Campaign Management Service](#campaignservice)  

## <a name="bulkservice"></a>Managing Advertising Settings with the Bulk Service
The [Bulk Service](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference.aspx) create, update, and delete operations can be completed using Bulk upload. You can use Bulk download to read back your data. For more information see [Bulk File Schema](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx) and [Bulk Download and Upload](../guides/bulk-download-and-upload.md).

These are the basic advertising entities that can be accessed using the [Bulk Service](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference.aspx).
-   [Campaign](https://msdn.microsoft.com/library/dn764752.aspx)  
-   [Ad Group](https://msdn.microsoft.com/library/dn764731.aspx)  
-   [Product Ad](https://msdn.microsoft.com/library/dn764755.aspx)  
-   [Text Ad](https://msdn.microsoft.com/library/dn764756.aspx)  
-   [Keyword](https://msdn.microsoft.com/library/dn764751.aspx)  

For code examples that show how to add campaigns, ad groups, ads, and keywords using the Bulk service, see [C&#35;](../guides/bulk-ads-and-keywords-in-csharp.md) | [Java](../guides/bulk-ads-and-keywords-in-java.md) | [Python](../guides/bulk-ads-and-keywords-in-python.md).

## <a name="campaignservice"></a>Managing Advertising Settings with the Campaign Management Service
These are the basic advertising entities that can be accessed using the [Campaign Management Service](https://msdn.microsoft.com/library/bing-ads-campaign-management-service-reference.aspx). You can create, read, update, and delete these entities.

> [!NOTE]
> Partial success is supported when adding, updating, and deleting these entities. For example if you submit 10 keywords and 2 fail, the remaining 8 will succeed. For more information, see [Partial Success using the Campaign Management Service](../guides/handling-service-errors-and-exceptions.md#partialsuccess).

|Entities|Create|Read|Update|Delete|
|------------|----------|--------|----------|----------|
|[Campaign](https://msdn.microsoft.com/library/bb672054.aspx)|[AddCampaigns](https://msdn.microsoft.com/library/dn277510.aspx)|[GetCampaignsByAccountId](https://msdn.microsoft.com/library/dn236299.aspx)<br /><br />[GetCampaignsByIds](https://msdn.microsoft.com/library/dn236303.aspx)|[UpdateCampaigns](https://msdn.microsoft.com/library/dn277536.aspx)|[DeleteCampaigns](https://msdn.microsoft.com/library/dn236314.aspx)|
|[AdGroup](https://msdn.microsoft.com/library/bb671956.aspx)|[AddAdGroups](https://msdn.microsoft.com/library/dn277502.aspx)|[GetAdGroupsByCampaignId](https://msdn.microsoft.com/library/dn277524.aspx)<br /><br />[GetAdGroupsByIds](https://msdn.microsoft.com/library/dn277529.aspx)|[UpdateAdGroups](https://msdn.microsoft.com/library/dn277528.aspx)|[DeleteAdGroups](https://msdn.microsoft.com/library/dn236307.aspx)|
|[ProductAd](https://msdn.microsoft.com/library/jj738612.aspx)<br /><br />[TextAd](https://msdn.microsoft.com/library/bb672081.aspx)|[AddAds](https://msdn.microsoft.com/library/dn277506.aspx)|[GetAdsByAdGroupId](https://msdn.microsoft.com/library/dn277534.aspx)<br /><br />[GetAdsByEditorialStatus](https://msdn.microsoft.com/library/dn277538.aspx)<br /><br />[GetAdsByIds](https://msdn.microsoft.com/library/dn236296.aspx)|[UpdateAds](https://msdn.microsoft.com/library/dn277531.aspx)|[DeleteAds](https://msdn.microsoft.com/library/dn236310.aspx)|
|[Keyword](https://msdn.microsoft.com/library/bb671833.aspx)|[AddKeywords](https://msdn.microsoft.com/library/dn277513.aspx)|[GetKeywordsByAdGroupId](https://msdn.microsoft.com/library/dn236311.aspx)<br /><br />[GetKeywordsByEditorialStatus](https://msdn.microsoft.com/library/dn277501.aspx)<br /><br />[GetKeywordsByIds](https://msdn.microsoft.com/library/dn277505.aspx)|[UpdateKeywords](https://msdn.microsoft.com/library/dn236295.aspx)|[DeleteKeywords](https://msdn.microsoft.com/library/dn236318.aspx)|

For code examples that show how to add campaigns, ad groups, ads, and keywords using the Campaign Management service, see [C&#35;](../guides/ads-and-keywords-in-csharp.md) | [Java](../guides/ads-and-keywords-in-java.md) | [PHP](../guides/ads-and-keywords-in-php.md) | [Python](../guides/ads-and-keywords-in-python.md).

## See Also
[Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md)

