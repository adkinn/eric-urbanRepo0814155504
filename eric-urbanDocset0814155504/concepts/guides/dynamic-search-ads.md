---
title: "Dynamic Search Ads"
ms.custom: na
ms.date: "08/10/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: cd594210-6e76-409b-b5db-ebd2979a9374
caps.latest.revision: 2
---
# Dynamic Search Ads
Dynamic Search Ads are coming to Bing Ads. You will be able to create a new type of campaign where the ad copy is automatically generated from the content on your website. 

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../../concepts/includes/pilot_comingsoon.md)]
> 
> Before you can use dynamic search ads, you must upgrade to Final Urls. For more information, see [URL Tracking with Upgraded URLs](https://msdn.microsoft.com/library/bing-ads-tracking-template-urls-guide.aspx).

## <a name="bulk"></a>Bulk API for Dynamic Search Ads  
The following Bulk records are added for managing dynamic search ads campaigns.
* [Ad Group Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-dynamic-search-ad-target-record(v=msads.100).aspx)
* [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record(v=msads.100).aspx)
* [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record(v=msads.100).aspx)
* [Dynamic Search Ad](https://msdn.microsoft.com/library/bing-ads-bulk-dynamic-search-ad-record(v=msads.100).aspx)
 
To get started with dynamic search ads, first you'll need to define a [Campaign](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-record(v=msads.100).aspx) record with the *Campaign Type* field set to *DynamicSearchAds*. When you create the campaign, you'll also need to specify the *Domain Language* and *Website* fields.  

Next, define an [Ad Group](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-record(v=msads.100).aspx) within the dynamic search ads campaign. You can add one or more [Ad Group Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-dynamic-search-ad-target-record(v=msads.100).aspx) records for the parent ad group that helps determine whether or not to serve dynamic search ads. 

If you want to exclude certain portions of your website, you can add negative targets at the campaign and/or ad group level using the respective [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record(v=msads.100).aspx) and [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record(v=msads.100).aspx) records. The [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record(v=msads.100).aspx) at the campaign level applies to all ad groups within the campaign; however, if you define ad group level [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record(v=msads.100).aspx), the campaign target is ignored for that ad group. 

For any of the [Ad Group Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-dynamic-search-ad-target-record(v=msads.100).aspx), [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record(v=msads.100).aspx), and [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record(v=msads.100).aspx) records, you can choose whether you want the target argument to match partial URLs, page content, page title, or categories that Bing thinks applies to your website. To discover the categories that you can use for targets (positive or negative), call the [GetDomainCategories](https://msdn.microsoft.com/library/bing-ads-ad-insight-getdomaincategories.aspx) operation with the Ad Insight service.

Finally you can define a [Dynamic Search Ad](https://msdn.microsoft.com/library/bing-ads-bulk-dynamic-search-ad-record(v=msads.100).aspx) record assigned to the ad group. The ad title and display URL are generated automatically based on the website domain and language that you want to target.


## <a name="campaign"></a>Campaign Management API for Dynamic Search Ads  

To get started with dynamic search ads, first you'll need to [add](https://msdn.microsoft.com/library/bing-ads-campaign-management-addcampaigns.aspx) a new [Campaign](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaign.aspx) with its type set to *DynamicSearchAds*. When you create the campaign, you'll need to include a [DynamicSearchAdsSetting](https://msdn.microsoft.com/library/bing-ads-campaign-management-dynamicsearchadssetting.aspx) that specifies the target website domain and language. The new *DynamicSearchAds* value is added to the [CampaignType](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaigntype.aspx) value set. 

Next, [create](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroups.aspx) a new [AdGroup](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroup.aspx) within the dynamic search ads campaign. You can add one or more [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion to each ad group that helps determine whether or not to serve dynamic search ads, by calling the [AddAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupcriterions.aspx) operation. 

If you want to exclude certain portions of your website, you can add negative [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion at the campaign and/or ad group level using the respective [AddCampaignCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addcampaigncriterions.aspx) and [AddAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupcriterions.aspx) service operations. The negative [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion at the campaign level applies to all ad groups within the campaign; however, if you define ad group level negative [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion, the campaign criterion is ignored for that ad group. 

Whether the criterion is positive or negative, you can choose whether you want the criterion argument to match partial URLs, page content, page title, or categories that Bing thinks applies to your website. To discover the categories that you can use for [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion (positive or negative), use the [GetDomainCategories](https://msdn.microsoft.com/library/bing-ads-ad-insight-getdomaincategories.aspx) operation with the Ad Insight service.

Finally you can [add](https://msdn.microsoft.com/library/bing-ads-campaign-management-addads.aspx) a [DynamicSearchAd](https://msdn.microsoft.com/library/bing-ads-campaign-management-dynamicsearchad.aspx) into the ad group. The ad title and display URL are generated automatically based on the website domain and language that you want to target.
