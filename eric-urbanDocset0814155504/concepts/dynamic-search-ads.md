---
title: "Dynamic Search Ads"
ms.custom: ""
ms.date: "08/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd594210-6e76-409b-b5db-ebd2979a9374
caps.latest.revision: 2
---
# Dynamic Search Ads
Dynamic Search Ads are coming to Bing Ads. You will be able to create a new type of campaign where the ad copy is automatically generated from the content on your website. 

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot-comingsoon.md)]
> 
> Before you can use dynamic search ads, you must upgrade to Final Urls. For more information, see [URL Tracking with Upgraded URLs](~/concepts/url-tracking-with-upgraded-urls.md).

## <a name="bulk"></a>Bulk API for Dynamic Search Ads  
The following Bulk records are added for managing dynamic search ads campaigns.
* [Ad Group Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-dynamic-search-ad-target-record(v=msads.100).aspx)
* [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record(v=msads.100).aspx)
* [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record(v=msads.100).aspx)
* [Dynamic Search Ad](https://msdn.microsoft.com/library/bing-ads-bulk-dynamic-search-ad-record(v=msads.100).aspx)
 
To get started with dynamic search ads, first you'll need to define a [Campaign](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-record(v=msads.100).aspx) record with the *Campaign Type* field set to *DynamicSearchAds*. When you create the campaign, you'll also need to specify the *Domain Language* and *Website* fields.  

Next, define an [Ad Group](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-record(v=msads.100).aspx) within the dynamic search ads campaign. You can add one or more [Ad Group Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-dynamic-search-ad-target-record(v=msads.100).aspx) records for the parent ad group that helps determine whether or not to serve dynamic search ads. 

If you want to exclude certain portions of your website, you can add negative targets at the campaign and/or ad group level using the respective [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record(v=msads.100).aspx) and [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record(v=msads.100).aspx) records. The [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record(v=msads.100).aspx) at the campaign level applies to all ad groups within the campaign; however, if you define ad group level [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record(v=msads.100).aspx), the campaign target is ignored for that ad group. 

For any of the [Ad Group Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-dynamic-search-ad-target-record(v=msads.100).aspx), [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record(v=msads.100).aspx), and [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record(v=msads.100).aspx) records, you can choose whether you want the target argument to match partial URLs, page content, page title, or categories that Bing thinks applies to your website. To discover the categories that you can use for targets (positive or negative), call the [GetDomainCategories](~/adinsight-api/getdomaincategories-service-operation.md) operation with the Ad Insight service.

Finally you can define a [Dynamic Search Ad](https://msdn.microsoft.com/library/bing-ads-bulk-dynamic-search-ad-record(v=msads.100).aspx) record assigned to the ad group. The ad title and display URL are generated automatically based on the website domain and language that you want to target.


## <a name="campaign"></a>Campaign Management API for Dynamic Search Ads  

To get started with dynamic search ads, first you'll need to [add](~/campaign-api/addcampaigns-service-operation.md) a new [Campaign](~/campaign-api/campaign-data-object.md) with its type set to *DynamicSearchAds*. When you create the campaign, you'll need to include a [DynamicSearchAdsSetting](~/campaign-api/dynamicsearchadssetting-data-object.md) that specifies the target website domain and language. The new *DynamicSearchAds* value is added to the [CampaignType](~/campaign-api/campaigntype-value-set.md) value set. 

Next, [create](~/campaign-api/addadgroups-service-operation.md) a new [AdGroup](~/campaign-api/adgroup-data-object.md) within the dynamic search ads campaign. You can add one or more [Webpage](~/campaign-api/webpage-data-object.md) criterion to each ad group that helps determine whether or not to serve dynamic search ads, by calling the [AddAdGroupCriterions](~/campaign-api/addadgroupcriterions-service-operation.md) operation. 

If you want to exclude certain portions of your website, you can add negative [Webpage](~/campaign-api/webpage-data-object.md) criterion at the campaign and/or ad group level using the respective [AddCampaignCriterions](~/campaign-api/addcampaigncriterions-service-operation.md) and [AddAdGroupCriterions](~/campaign-api/addadgroupcriterions-service-operation.md) service operations. The negative [Webpage](~/campaign-api/webpage-data-object.md) criterion at the campaign level applies to all ad groups within the campaign; however, if you define ad group level negative [Webpage](~/campaign-api/webpage-data-object.md) criterion, the campaign criterion is ignored for that ad group. 

Whether the criterion is positive or negative, you can choose whether you want the criterion argument to match partial URLs, page content, page title, or categories that Bing thinks applies to your website. To discover the categories that you can use for [Webpage](~/campaign-api/webpage-data-object.md) criterion (positive or negative), use the [GetDomainCategories](~/adinsight-api/getdomaincategories-service-operation.md) operation with the Ad Insight service.

Finally you can [add](~/campaign-api/addads-service-operation.md) a [DynamicSearchAd](~/campaign-api/dynamicsearchad-data-object.md) into the ad group. The ad title and display URL are generated automatically based on the website domain and language that you want to target.
